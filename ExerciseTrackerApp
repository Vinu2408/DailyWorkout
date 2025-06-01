import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";

export default function ExerciseTracker() {
  const [entries, setEntries] = useState([]);
  const [form, setForm] = useState({
    date: "",
    exercise: "",
    setsReps: "",
    weight: "",
    notes: "",
    progress: "✔️"
  });
  const [editIndex, setEditIndex] = useState(null);

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
  };

  const addEntry = () => {
    if (editIndex !== null) {
      const updatedEntries = [...entries];
      updatedEntries[editIndex] = form;
      setEntries(updatedEntries);
      setEditIndex(null);
    } else {
      setEntries([...entries, form]);
    }
    setForm({ date: "", exercise: "", setsReps: "", weight: "", notes: "", progress: "✔️" });
  };

  const editEntry = (index) => {
    setForm(entries[index]);
    setEditIndex(index);
  };

  const deleteEntry = (index) => {
    const filtered = entries.filter((_, i) => i !== index);
    setEntries(filtered);
    if (editIndex === index) {
      setForm({ date: "", exercise: "", setsReps: "", weight: "", notes: "", progress: "✔️" });
      setEditIndex(null);
    }
  };

  return (
    <div className="p-4 max-w-xl mx-auto">
      <h1 className="text-2xl font-bold mb-4">🏋️ Exercise Progress Tracker</h1>

      <div className="grid gap-2 mb-4">
        <Input name="date" placeholder="Date (YYYY-MM-DD)" value={form.date} onChange={handleChange} />
        <Input name="exercise" placeholder="Exercise" value={form.exercise} onChange={handleChange} />
        <Input name="setsReps" placeholder="Sets & Reps / Time" value={form.setsReps} onChange={handleChange} />
        <Input name="weight" placeholder="Weight (kg/lb)" value={form.weight} onChange={handleChange} />
        <Textarea name="notes" placeholder="Notes" value={form.notes} onChange={handleChange} />
        <select name="progress" value={form.progress} onChange={handleChange} className="p-2 border rounded">
          <option value="✔️">✔️ Maintained</option>
          <option value="⬆️">⬆️ Improved</option>
          <option value="⬇️">⬇️ Struggled</option>
        </select>
        <Button onClick={addEntry}>{editIndex !== null ? "Update Entry" : "Add Entry"}</Button>
      </div>

      <div className="space-y-4">
        {entries.map((entry, idx) => (
          <Card key={idx}>
            <CardContent className="p-4 space-y-2">
              <p><strong>{entry.date}</strong> - {entry.exercise}</p>
              <p>{entry.setsReps} | {entry.weight}</p>
              <p className="text-sm italic">{entry.notes}</p>
              <p className="text-xl">{entry.progress}</p>
              <div className="flex gap-2">
                <Button variant="secondary" onClick={() => editEntry(idx)}>Edit</Button>
                <Button variant="destructive" onClick={() => deleteEntry(idx)}>Delete</Button>
              </div>
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}
