import React, { useState, useEffect, useMemo } from 'react';
import { 
  LineChart, Line, AreaChart, Area, BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer, PieChart, Pie, Cell, ReferenceLine, RadarChart, PolarGrid, PolarAngleAxis, PolarRadiusAxis, Radar, Legend, ComposedChart, Scatter
} from 'recharts';
import { 
  Activity, AlertTriangle, Box, Truck, Zap, Wrench, Users, ClipboardCheck, 
  Settings, Search, Bell, Menu, Cpu, Factory, Anchor, Layers, Clock, 
  TrendingUp, Wifi, CheckCircle, XCircle, AlertOctagon, Package, ArrowRight,
  Database, ShieldCheck, DollarSign, FileText, Scan, ShoppingCart, UserCheck,
  BarChart2, Lock, Scale, Calendar, MapPin, Printer, Share2, FileCheck, Brain,
  History, Thermometer, Droplet, Gauge, Ban
} from 'lucide-react';

// --- THEME & CONSTANTS ---

const COLORS = {
  primary: '#06b6d4', // Cyan 500
  success: '#10b981', // Emerald 500
  warning: '#f59e0b', // Amber 500
  danger: '#ef4444', // Red 500
  dark: '#0f172a', // Slate 900
  card: '#1e293b', // Slate 800
  text: '#f1f5f9', // Slate 100
  muted: '#64748b', // Slate 500
  accent: '#6366f1', // Indigo 500
  purple: '#a855f7', // Purple 500
  pink: '#ec4899'   // Pink 500
};

// --- MOCK DATA GENERATORS ---

const generateId = (prefix) => `${prefix}-${Math.floor(Math.random() * 9000) + 1000}`;

const INITIAL_TRUCKS = [
  { id: 'TRK-9001', plate: 'KA-01-HH-1234', vendor: 'SteelCo Ltd', material: 'Steel Sheets', po: 'PO-2201', status: 'Waiting', time: '10:00 AM', damage: false },
  { id: 'TRK-9002', plate: 'MH-04-AB-9876', vendor: 'PolyChem', material: 'Resin-X', po: 'PO-2205', status: 'Gate Entry', time: '10:15 AM', damage: false },
  { id: 'TRK-9003', plate: 'TN-09-XZ-4455', vendor: 'Unapproved Vendor', material: 'Lubricants', po: 'N/A', status: 'Rejected', time: '10:30 AM', damage: false },
];

const INITIAL_INVOICES = [
  { id: 'INV-8821', vendor: 'SteelCo Ltd', amount: 45000, tax: 8100, status: 'Pending Match', po: 'PO-2201', discrepancy: false },
  { id: 'INV-8822', vendor: 'PolyChem', amount: 12000, tax: 2160, status: 'Pending Match', po: 'PO-2205', discrepancy: true },
];

const INITIAL_MACHINES = [
  { id: 'CNC-01', name: 'Milling A', status: 'Running', oee: 88, temp: 65, vib: 2.1, operator: 'Rajesh K.', utilization: [60, 65, 70, 80, 88, 88] },
  { id: 'CNC-02', name: 'Milling B', status: 'Breakdown', oee: 45, temp: 82, vib: 5.4, operator: 'Wait Maint.', utilization: [60, 55, 40, 20, 0, 0] },
  { id: 'PRESS-01', name: 'Hydraulic Press', status: 'Running', oee: 92, temp: 58, vib: 1.2, operator: 'Sarah L.', utilization: [80, 82, 85, 90, 92, 92] },
  { id: 'ROBO-01', name: 'Welding Bot', status: 'Idle', oee: 78, temp: 45, vib: 0.5, operator: 'Auto', utilization: [50, 50, 40, 30, 10, 0] },
];

const SKILL_MATRIX = [
  { name: 'Rajesh K.', role: 'Operator', skills: { CNC: 90, Welding: 40, QC: 60 }, shift: 'Morning', status: 'Active' },
  { name: 'Sarah L.', role: 'Senior Op', skills: { CNC: 85, Welding: 80, QC: 95 }, shift: 'Morning', status: 'Active' },
  { name: 'Mike T.', role: 'Technician', skills: { CNC: 50, Maintenance: 95, QC: 40 }, shift: 'Night', status: 'Off-Shift' },
];

const MATERIAL_REQUESTS = [
  { id: 'MR-101', mo: 'MO-8821', item: 'Steel Sheet 2mm', qty: 500, issued: 0, status: 'Pending', requiredDate: 'Today' },
  { id: 'MR-102', mo: 'MO-8821', item: 'Coolant Type-A', qty: 50, issued: 50, status: 'Issued', requiredDate: 'Today' },
  { id: 'MR-103', mo: 'MO-8824', item: 'Packaging Box L', qty: 1000, issued: 0, status: 'Pending', requiredDate: 'Tomorrow' },
];

const FINISHED_GOODS = [
  { id: 'FG-001', sku: 'AutoPart-X', batch: 'B-2201', qty: 1200, location: 'A-01', status: 'QC Pass' },
  { id: 'FG-002', sku: 'AutoPart-Y', batch: 'B-2202', qty: 850, location: 'A-02', status: 'QC Hold' },
];

const VENDORS = [
  { id: 'V-101', name: 'SteelCo Ltd', rating: 4.8, status: 'Active', spending: 125000, lastDelivery: 'On Time' },
  { id: 'V-102', name: 'PolyChem', rating: 3.2, status: 'Probation', spending: 45000, lastDelivery: 'Late' },
  { id: 'V-103', name: 'Global Bolts', rating: 4.5, status: 'Active', spending: 12000, lastDelivery: 'On Time' },
];

const COMPLIANCE_LOGS = [
  { id: 1, type: 'Safety', desc: 'Fire Extinguisher Expired - Zone B', status: 'Critical', date: '2023-10-24' },
  { id: 2, type: 'Environment', desc: 'Effluent Treatment Plant (ETP) pH Level Normal', status: 'Pass', date: '2023-10-24' },
  { id: 3, type: 'Labor', desc: 'Shift Overtime Limits Checked', status: 'Pass', date: '2023-10-23' },
];

const AI_PREDICTIONS = [
  { model: 'Predictive Maintenance', target: 'CNC-02', probability: 89, impact: 'High', suggestion: 'Replace Spindle Bearing' },
  { model: 'Demand Forecast', target: 'Resin-X', probability: 75, impact: 'Medium', suggestion: 'Increase Order +20%' },
  { model: 'QC Defect', target: 'Line-1', probability: 92, impact: 'High', suggestion: 'Calibrate Camera Exposure' },
];

// --- REUSABLE COMPONENTS ---

const Card = ({ children, title, action, className = "", noPadding = false, alert = false }) => (
  <div className={`bg-slate-800 border ${alert ? 'border-rose-500/50 animate-pulse' : 'border-slate-700'} rounded-lg shadow-lg flex flex-col ${className}`}>
    <div className="flex justify-between items-center p-4 border-b border-slate-700 bg-slate-800/50">
      <h3 className="text-slate-200 font-semibold flex items-center gap-2">
        {title}
      </h3>
      {action && <div className="text-sm">{action}</div>}
    </div>
    <div className={`flex-1 ${noPadding ? '' : 'p-4'}`}>
      {children}
    </div>
  </div>
);

const Button = ({ children, onClick, variant = 'primary', size = 'md', className = '', disabled = false }) => {
  const base = "font-medium rounded transition-all flex items-center justify-center gap-2 disabled:opacity-50 disabled:cursor-not-allowed";
  const sizes = { sm: 'px-2 py-1 text-xs', md: 'px-4 py-2 text-sm', lg: 'px-6 py-3 text-base' };
  const variants = {
    primary: 'bg-cyan-600 hover:bg-cyan-500 text-white shadow-lg shadow-cyan-500/20',
    secondary: 'bg-slate-700 hover:bg-slate-600 text-slate-200 border border-slate-600',
    danger: 'bg-rose-600 hover:bg-rose-500 text-white shadow-lg shadow-rose-500/20',
    success: 'bg-emerald-600 hover:bg-emerald-500 text-white shadow-lg shadow-emerald-500/20',
    ghost: 'bg-transparent hover:bg-slate-700 text-slate-400 hover:text-white',
    warning: 'bg-amber-600 hover:bg-amber-500 text-white shadow-lg shadow-amber-500/20'
  };

  return (
    <button onClick={onClick} disabled={disabled} className={`${base} ${sizes[size]} ${variants[variant]} ${className}`}>
      {children}
    </button>
  );
};

const StatBadge = ({ status }) => {
  const styles = {
    Running: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Active: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Completed: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Approved: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Matched: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Pass: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Issued: 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20',
    Waiting: 'bg-amber-500/10 text-amber-400 border-amber-500/20',
    Pending: 'bg-amber-500/10 text-amber-400 border-amber-500/20',
    Warning: 'bg-amber-500/10 text-amber-400 border-amber-500/20',
    Probation: 'bg-amber-500/10 text-amber-400 border-amber-500/20',
    Idle: 'bg-slate-600/20 text-slate-400 border-slate-500/20',
    Breakdown: 'bg-rose-500/10 text-rose-400 border-rose-500/20',
    Rejected: 'bg-rose-500/10 text-rose-400 border-rose-500/20',
    Critical: 'bg-rose-500/10 text-rose-400 border-rose-500/20',
    'QC Hold': 'bg-rose-500/10 text-rose-400 border-rose-500/20',
    'Pending Match': 'bg-blue-500/10 text-blue-400 border-blue-500/20',
  };
  
  return (
    <span className={`px-2 py-1 rounded text-[10px] uppercase tracking-wider border ${styles[status] || styles['Idle']} font-semibold`}>
      {status}
    </span>
  );
};

// --- MAIN APPLICATION ---

const App = () => {
  // --- STATE MANAGEMENT ---
  const [activeTab, setActiveTab] = useState('Overview');
  const [currentTime, setCurrentTime] = useState(new Date().toLocaleTimeString());
  const [notifications, setNotifications] = useState([
    { id: 1, type: 'warning', msg: 'Low stock: Resin-X (Critical)', time: '10:05 AM' },
    { id: 2, type: 'danger', msg: 'CNC-02 Breakdown: Vibration Limit Exceeded', time: '09:45 AM' }
  ]);

  // Operational Data States
  const [trucks, setTrucks] = useState(INITIAL_TRUCKS);
  const [invoices, setInvoices] = useState(INITIAL_INVOICES);
  const [machines, setMachines] = useState(INITIAL_MACHINES);
  const [inventory, setInventory] = useState(Array.from({ length: 12 }, (_, i) => ({ id: `BIN-${100+i}`, sku: `MAT-${10+i}`, qty: Math.floor(Math.random()*500), capacity: 1000 })));
  const [dispatchOrders, setDispatchOrders] = useState([
    { id: 'DO-5501', customer: 'AutoCorp', items: 150, status: 'Picking' },
    { id: 'DO-5502', customer: 'Global Motors', items: 400, status: 'Ready to Ship' }
  ]);
  const [materialRequests, setMaterialRequests] = useState(MATERIAL_REQUESTS);
  const [finishedGoods, setFinishedGoods] = useState(FINISHED_GOODS);
  const [vendors, setVendors] = useState(VENDORS);
  const [financeData, setFinanceData] = useState({
    pendingPayments: [
      { id: 'PAY-001', vendor: 'SteelCo Ltd', amount: 45000, due: 'Today', status: 'Pending' },
      { id: 'PAY-002', vendor: 'Global Bolts', amount: 12000, due: 'Tomorrow', status: 'Approved' },
    ]
  });

  useEffect(() => {
    const timer = setInterval(() => setCurrentTime(new Date().toLocaleTimeString()), 1000);
    return () => clearInterval(timer);
  }, []);

  // --- ACTIONS ---

  const addNotification = (type, msg) => {
    const newNotif = { id: Date.now(), type, msg, time: new Date().toLocaleTimeString() };
    setNotifications(prev => [newNotif, ...prev]);
  };

  const handleGateEntry = () => {
    const newTruck = { 
      id: generateId('TRK'), 
      plate: 'New-Arrival', 
      vendor: 'Pending Ident', 
      material: 'Raw Material', 
      po: 'Scanning...', 
      status: 'Gate Entry', 
      time: new Date().toLocaleTimeString(), 
      damage: false 
    };
    setTrucks(prev => [newTruck, ...prev]);
    addNotification('info', 'New Truck Detected at Gate A (ANPR Scan)');
  };

  const verifyTruck = (id) => {
    setTrucks(prev => prev.map(t => t.id === id ? { ...t, status: 'Approved', vendor: 'Verified Vendor', po: 'PO-MATCHED' } : t));
    addNotification('success', `Truck ${id} Verified. 3-Way Match Initiated.`);
  };

  const createGRN = (invId) => {
    setInvoices(prev => prev.map(i => i.id === invId ? { ...i, status: 'Matched' } : i));
    addNotification('success', `GRN Generated for ${invId}. Inventory Updated.`);
    setInventory(prev => prev.map((item, idx) => idx === 0 ? { ...item, qty: item.qty + 100 } : item));
  };

  const triggerMaintenance = (machineId) => {
    setMachines(prev => prev.map(m => m.id === machineId ? { ...m, status: 'Maintenance' } : m));
    addNotification('warning', `Maintenance Ticket Created for ${machineId}. Technician Dispatched.`);
  };

  const generateEWayBill = (orderId) => {
    setDispatchOrders(prev => prev.map(o => o.id === orderId ? { ...o, status: 'Shipped' } : o));
    addNotification('success', `E-Way Bill Generated for ${orderId}. Driver OTP Sent.`);
  };

  const issueMaterial = (reqId) => {
    setMaterialRequests(prev => prev.map(r => r.id === reqId ? { ...r, status: 'Issued', issued: r.qty } : r));
    addNotification('success', `Material Request ${reqId} Issued. Stock Deducted.`);
  };

  const approvePayment = (payId) => {
    setFinanceData(prev => ({
      ...prev,
      pendingPayments: prev.pendingPayments.map(p => p.id === payId ? { ...p, status: 'Approved' } : p)
    }));
    addNotification('success', `Payment ${payId} Approved for Disbursement.`);
  };

  const acknowledgeAlert = (id) => {
    setNotifications(prev => prev.filter(n => n.id !== id));
  };

  // --- NAVIGATION ---
  
  const navGroups = [
    {
      title: 'Operations',
      items: [
        { name: 'Overview', icon: Activity },
        { name: 'Live Floor', icon: Factory },
        { name: 'Alert Center', icon: Bell }
      ]
    },
    {
      title: 'Inbound',
      items: [
        { name: 'Gate Entry', icon: Truck },
        { name: 'GRN & Billing', icon: FileText }
      ]
    },
    {
      title: 'Materials',
      items: [
        { name: 'Stores', icon: Package },
        { name: 'Material Issue', icon: ShoppingCart },
        { name: 'Output & FG', icon: Box }
      ]
    },
    {
      title: 'Production',
      items: [
        { name: 'Quality Control', icon: ShieldCheck },
        { name: 'Maintenance', icon: Wrench },
        { name: 'Workforce', icon: Users }
      ]
    },
    {
      title: 'Outbound',
      items: [
        { name: 'Dispatch', icon: Anchor },
        { name: 'Finance', icon: DollarSign }
      ]
    },
    {
      title: 'Strategy',
      items: [
        { name: 'Vendor Mgmt', icon: UserCheck },
        { name: 'Compliance', icon: Lock },
        { name: 'AI Engine', icon: Cpu }
      ]
    }
  ];

  // --- VIEW RENDERERS ---

  const renderOverview = () => (
    <div className="grid grid-cols-1 md:grid-cols-4 gap-6">
      <Card title="Plant OEE" className="md:col-span-1">
        <div className="flex items-end gap-2 mb-2">
          <span className="text-4xl font-bold text-white">78.4%</span>
          <span className="text-sm text-rose-400">▼ 2.1%</span>
        </div>
        <ResponsiveContainer width="100%" height={60}>
          <AreaChart data={[{v:70},{v:75},{v:72},{v:78},{v:76},{v:82},{v:78}]}>
            <Area type="monotone" dataKey="v" stroke={COLORS.primary} fill={COLORS.primary} fillOpacity={0.2} />
          </AreaChart>
        </ResponsiveContainer>
      </Card>

      <Card title="Production Rate" className="md:col-span-1">
        <div className="flex items-end gap-2 mb-2">
          <span className="text-4xl font-bold text-white">1,240</span>
          <span className="text-sm text-emerald-400">Units/Hr</span>
        </div>
        <div className="w-full bg-slate-700 h-2 rounded-full mt-4">
          <div className="bg-emerald-500 h-full rounded-full" style={{ width: '85%' }}></div>
        </div>
        <div className="text-xs text-slate-400 mt-2 text-center">85% of Shift Target</div>
      </Card>

      <Card title="Critical Alerts" className="md:col-span-2" alert={notifications.length > 5}>
        <div className="h-24 overflow-y-auto pr-2 custom-scrollbar space-y-2">
          {notifications.slice(0, 3).map(n => (
            <div key={n.id} className={`p-2 rounded border-l-4 text-xs flex justify-between ${n.type === 'danger' ? 'bg-rose-900/20 border-rose-500' : 'bg-amber-900/20 border-amber-500'}`}>
              <span className="text-slate-200">{n.msg}</span>
              <span className="text-slate-500 font-mono">{n.time}</span>
            </div>
          ))}
          {notifications.length > 3 && <div className="text-xs text-center text-slate-500">View All in Alert Center</div>}
        </div>
      </Card>

      <Card title="Live Factory Twin" className="md:col-span-4 h-96">
        <div className="grid grid-cols-4 gap-4 h-full">
          {machines.map(m => (
            <div key={m.id} className={`relative p-4 rounded border transition-all ${m.status === 'Running' ? 'bg-slate-700/30 border-emerald-500/50' : m.status === 'Breakdown' ? 'bg-rose-900/20 border-rose-500' : 'bg-slate-800 border-slate-700'}`}>
              <div className="flex justify-between mb-2">
                <span className="font-mono text-xs text-slate-400">{m.id}</span>
                <StatBadge status={m.status} />
              </div>
              <div className="text-lg font-bold text-white mb-4">{m.name}</div>
              <div className="grid grid-cols-2 gap-2 text-xs text-slate-400">
                <div>OEE: <span className="text-white">{m.oee}%</span></div>
                <div>Temp: <span className={m.temp > 80 ? 'text-rose-400' : 'text-emerald-400'}>{m.temp}°C</span></div>
                <div>Vib: <span className={m.vib > 4 ? 'text-rose-400' : 'text-emerald-400'}>{m.vib} mm/s</span></div>
                <div>Op: <span className="text-white">{m.operator}</span></div>
              </div>
              {m.status === 'Breakdown' && (
                <Button variant="secondary" size="sm" className="w-full mt-4" onClick={() => triggerMaintenance(m.id)}>
                  <Wrench size={12} /> Assign Tech
                </Button>
              )}
            </div>
          ))}
        </div>
      </Card>
    </div>
  );

  const renderGateEntry = () => (
    <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
      <Card title="Live Gate Camera Feed (ANPR)" className="lg:col-span-1 h-64 lg:h-auto">
        <div className="bg-black relative h-full rounded flex items-center justify-center overflow-hidden border border-slate-700 group">
          <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1587293852726-70cdb56c2866?auto=format&fit=crop&q=80')] bg-cover bg-center opacity-40"></div>
          <Scan className="w-16 h-16 text-cyan-400 animate-pulse relative z-10" />
          <div className="absolute bottom-4 left-4 bg-slate-900/80 p-2 rounded border border-cyan-500/30 backdrop-blur z-20">
            <div className="text-[10px] text-cyan-400 uppercase">Recognized Plate</div>
            <div className="text-xl font-mono font-bold text-white">MH-04-AB-9876</div>
          </div>
          <div className="absolute top-4 right-4 z-20">
            <Button size="sm" onClick={handleGateEntry}>Simulate Arrival</Button>
          </div>
        </div>
      </Card>

      <Card title="Truck Queue & Verification" className="lg:col-span-2">
        <div className="overflow-x-auto">
          <table className="w-full text-sm text-left">
            <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
              <tr>
                <th className="p-3">Plate No</th>
                <th className="p-3">Vendor</th>
                <th className="p-3">Status</th>
                <th className="p-3">Time</th>
                <th className="p-3">Action</th>
              </tr>
            </thead>
            <tbody className="divide-y divide-slate-700">
              {trucks.map(t => (
                <tr key={t.id} className="hover:bg-slate-700/20">
                  <td className="p-3 font-mono text-cyan-400">{t.plate}</td>
                  <td className="p-3">{t.vendor}</td>
                  <td className="p-3"><StatBadge status={t.status} /></td>
                  <td className="p-3 text-slate-400">{t.time}</td>
                  <td className="p-3">
                    {t.status === 'Gate Entry' && (
                      <div className="flex gap-2">
                        <Button size="sm" variant="success" onClick={() => verifyTruck(t.id)}>Verify</Button>
                        <Button size="sm" variant="danger" onClick={() => addNotification('danger', `Truck ${t.plate} Rejected at Gate`)}>Reject</Button>
                      </div>
                    )}
                  </td>
                </tr>
              ))}
            </tbody>
          </table>
        </div>
      </Card>
    </div>
  );

  const renderGRN = () => (
    <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
      <Card title="Pending Invoices (3-Way Match)" className="lg:col-span-2">
        {invoices.map(inv => (
          <div key={inv.id} className="mb-3 p-4 bg-slate-700/30 rounded border border-slate-600 flex justify-between items-center">
            <div>
              <div className="flex items-center gap-2">
                <span className="font-bold text-white">{inv.id}</span>
                <span className="text-sm text-slate-400">({inv.vendor})</span>
              </div>
              <div className="text-xs text-slate-500 mt-1">PO: {inv.po} | Tax: ${inv.tax}</div>
            </div>
            <div className="text-right">
              <div className="text-xl font-bold text-white">${inv.amount.toLocaleString()}</div>
              {inv.status === 'Pending Match' ? (
                inv.discrepancy ? (
                   <div className="text-xs text-rose-400 flex items-center gap-1 justify-end mt-1"><AlertTriangle size={12}/> Rate Mismatch</div>
                ) : (
                  <Button size="sm" variant="primary" className="mt-2" onClick={() => createGRN(inv.id)}>Match & Create GRN</Button>
                )
              ) : (
                <StatBadge status="Matched" />
              )}
            </div>
          </div>
        ))}
      </Card>
      
      <Card title="Vendor Scorecard">
        <div className="flex flex-col items-center justify-center h-full">
           <ResponsiveContainer width="100%" height={200}>
             <RadarChart outerRadius={70} data={[
               { subject: 'On-Time', A: 120, fullMark: 150 },
               { subject: 'Quality', A: 98, fullMark: 150 },
               { subject: 'Cost', A: 86, fullMark: 150 },
               { subject: 'Compliance', A: 99, fullMark: 150 },
               { subject: 'Safety', A: 85, fullMark: 150 },
             ]}>
               <PolarGrid stroke="#334155" />
               <PolarAngleAxis dataKey="subject" tick={{ fill: '#94a3b8', fontSize: 10 }} />
               <PolarRadiusAxis angle={30} domain={[0, 150]} tick={false} axisLine={false} />
               <Radar name="SteelCo" dataKey="A" stroke={COLORS.primary} fill={COLORS.primary} fillOpacity={0.4} />
               <Legend />
             </RadarChart>
           </ResponsiveContainer>
        </div>
      </Card>
    </div>
  );

  const renderStores = () => (
    <div className="space-y-6">
      <div className="grid grid-cols-2 md:grid-cols-6 gap-4">
         {inventory.map((bin) => (
           <div key={bin.id} className="bg-slate-800 border border-slate-700 p-3 rounded hover:border-cyan-500 cursor-pointer relative group">
              <div className="text-xs text-slate-500">{bin.id}</div>
              <div className="text-sm font-bold text-white mt-1">{bin.sku}</div>
              <div className="mt-2 h-1.5 bg-slate-700 rounded-full overflow-hidden">
                <div className={`h-full ${bin.qty < 200 ? 'bg-rose-500' : 'bg-emerald-500'}`} style={{ width: `${(bin.qty/bin.capacity)*100}%` }}></div>
              </div>
              <div className="text-[10px] text-right mt-1 text-slate-400">{bin.qty} / {bin.capacity}</div>
              <div className="absolute inset-0 bg-slate-900/90 hidden group-hover:flex flex-col items-center justify-center gap-2 rounded transition-opacity">
                 <Button size="sm" variant="ghost" onClick={() => addNotification('info', `Cycle Count requested for ${bin.id}`)}>Count</Button>
                 {bin.qty < 200 && <Button size="sm" variant="primary" onClick={() => addNotification('success', `PO Auto-Drafted for ${bin.sku}`)}>Reorder</Button>}
              </div>
           </div>
         ))}
      </div>
      <Card title="Material Aging Analysis">
         <ResponsiveContainer width="100%" height={200}>
            <BarChart data={[
              { name: '0-30 Days', val: 4000 },
              { name: '31-60 Days', val: 3000 },
              { name: '61-90 Days', val: 2000 },
              { name: '>90 Days (Slow)', val: 500, alert: true },
            ]}>
              <CartesianGrid strokeDasharray="3 3" stroke="#334155" />
              <XAxis dataKey="name" stroke="#94a3b8" />
              <YAxis stroke="#94a3b8" />
              <Tooltip cursor={{fill: '#334155'}} contentStyle={{backgroundColor: '#1e293b', borderColor: '#475569'}} />
              <Bar dataKey="val">
                {[{val:4000}, {val:3000}, {val:2000}, {val:500}].map((entry, index) => (
                    <Cell key={`cell-${index}`} fill={index === 3 ? COLORS.danger : COLORS.primary} />
                ))}
              </Bar>
            </BarChart>
         </ResponsiveContainer>
      </Card>
    </div>
  );

  const renderMaterialIssue = () => (
    <div className="space-y-6">
      <Card title="Production Material Requests (BOM Driven)">
        <table className="w-full text-sm text-left">
          <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
            <tr>
              <th className="p-3">Req ID</th>
              <th className="p-3">Prod. Order</th>
              <th className="p-3">Material Item</th>
              <th className="p-3">Qty</th>
              <th className="p-3">Status</th>
              <th className="p-3">Action</th>
            </tr>
          </thead>
          <tbody className="divide-y divide-slate-700">
            {materialRequests.map(req => (
              <tr key={req.id} className="hover:bg-slate-700/20">
                <td className="p-3 font-mono text-cyan-400">{req.id}</td>
                <td className="p-3">{req.mo}</td>
                <td className="p-3">{req.item}</td>
                <td className="p-3">{req.qty}</td>
                <td className="p-3"><StatBadge status={req.status} /></td>
                <td className="p-3">
                  {req.status === 'Pending' ? (
                    <Button size="sm" variant="primary" onClick={() => issueMaterial(req.id)}>
                      <Box size={14} /> Issue
                    </Button>
                  ) : (
                    <span className="text-emerald-400 text-xs flex items-center gap-1"><CheckCircle size={14}/> Dispensed</span>
                  )}
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </Card>
      <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
         <Card title="BOM Deviation Tracker">
            <ResponsiveContainer width="100%" height={200}>
              <LineChart data={[
                 { day: 'Mon', planned: 100, actual: 102 },
                 { day: 'Tue', planned: 120, actual: 118 },
                 { day: 'Wed', planned: 110, actual: 125 }, // Spike
                 { day: 'Thu', planned: 130, actual: 132 },
                 { day: 'Fri', planned: 125, actual: 124 },
              ]}>
                 <CartesianGrid strokeDasharray="3 3" stroke="#334155" />
                 <XAxis dataKey="day" stroke="#94a3b8" />
                 <YAxis stroke="#94a3b8" />
                 <Tooltip contentStyle={{backgroundColor: '#1e293b', borderColor: '#475569'}} />
                 <Legend />
                 <Line type="monotone" dataKey="planned" stroke={COLORS.muted} strokeDasharray="5 5" />
                 <Line type="monotone" dataKey="actual" stroke={COLORS.danger} />
              </LineChart>
            </ResponsiveContainer>
         </Card>
         <Card title="Scrap & Return Management">
            <div className="flex flex-col gap-3">
               <div className="p-3 border border-slate-700 rounded bg-slate-800/50 flex justify-between items-center">
                  <div>
                    <div className="text-sm font-bold text-white">Metal Shavings</div>
                    <div className="text-xs text-slate-400">Bin: S-01</div>
                  </div>
                  <div className="text-right">
                    <div className="text-lg font-bold text-amber-400">45 kg</div>
                    <div className="text-xs text-slate-500">Unprocessed</div>
                  </div>
               </div>
               <div className="p-3 border border-slate-700 rounded bg-slate-800/50 flex justify-between items-center">
                  <div>
                    <div className="text-sm font-bold text-white">Defective Resin</div>
                    <div className="text-xs text-slate-400">Bin: S-04</div>
                  </div>
                  <div className="text-right">
                    <div className="text-lg font-bold text-rose-400">12 kg</div>
                    <Button size="sm" variant="ghost" className="text-xs">Log Disposal</Button>
                  </div>
               </div>
            </div>
         </Card>
      </div>
    </div>
  );

  const renderLiveFloor = () => (
    <div className="space-y-6">
      <div className="flex justify-between items-center">
        <h3 className="text-lg font-bold text-white">Digital Twin - Zone A</h3>
        <div className="flex gap-2">
           <Button size="sm" variant="secondary"><Settings size={14}/> View Logic</Button>
           <Button size="sm" variant="secondary"><Layers size={14}/> 3D Mode</Button>
        </div>
      </div>
      <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
        {machines.map(m => (
          <Card key={m.id} title={`${m.name} (${m.id})`}>
            <div className="flex gap-4 mb-4">
               <div className="w-1/3">
                  <div className={`w-full aspect-square rounded flex items-center justify-center border-4 ${m.status === 'Running' ? 'border-emerald-500 bg-emerald-900/20' : m.status === 'Breakdown' ? 'border-rose-500 bg-rose-900/20' : 'border-slate-500 bg-slate-800'}`}>
                     <Settings className={`w-16 h-16 ${m.status === 'Running' ? 'animate-spin text-emerald-400' : 'text-slate-500'}`} />
                  </div>
                  <div className="mt-2 text-center text-xl font-bold text-white">{m.status}</div>
               </div>
               <div className="w-2/3 space-y-2">
                  <div className="flex justify-between text-sm border-b border-slate-700 pb-1">
                     <span className="text-slate-400">Current Job</span>
                     <span className="text-white">MO-8821 (Bracket)</span>
                  </div>
                  <div className="flex justify-between text-sm border-b border-slate-700 pb-1">
                     <span className="text-slate-400">Operator</span>
                     <span className="text-white">{m.operator}</span>
                  </div>
                  <div className="flex justify-between text-sm border-b border-slate-700 pb-1">
                     <span className="text-slate-400">Performance</span>
                     <span className={`${m.oee < 70 ? 'text-rose-400' : 'text-emerald-400'}`}>{m.oee}% OEE</span>
                  </div>
                  <div className="mt-2 h-16">
                     <ResponsiveContainer width="100%" height="100%">
                        <BarChart data={m.utilization.map((u, i) => ({ val: u, time: i }))}>
                           <Bar dataKey="val" fill={m.status === 'Breakdown' ? COLORS.danger : COLORS.primary} />
                        </BarChart>
                     </ResponsiveContainer>
                  </div>
               </div>
            </div>
            <div className="grid grid-cols-3 gap-2">
               <div className="p-2 bg-slate-900/50 rounded text-center">
                  <div className="text-xs text-slate-500">Vibration</div>
                  <div className={`font-mono ${m.vib > 5 ? 'text-rose-500 animate-pulse' : 'text-white'}`}>{m.vib}</div>
               </div>
               <div className="p-2 bg-slate-900/50 rounded text-center">
                  <div className="text-xs text-slate-500">Temp</div>
                  <div className={`font-mono ${m.temp > 80 ? 'text-amber-500' : 'text-white'}`}>{m.temp}°C</div>
               </div>
               <div className="p-2 bg-slate-900/50 rounded text-center">
                  <div className="text-xs text-slate-500">Power</div>
                  <div className="text-white font-mono">12.4 kW</div>
               </div>
            </div>
          </Card>
        ))}
      </div>
    </div>
  );

  const renderAlertCenter = () => (
    <Card title="Central Alert Management System">
       <div className="flex justify-between mb-4">
          <div className="flex gap-2">
             <Button size="sm" variant="secondary">All</Button>
             <Button size="sm" variant="danger">Critical</Button>
             <Button size="sm" variant="warning">Warnings</Button>
          </div>
          <div className="relative">
             <Search size={16} className="absolute left-2 top-2 text-slate-400" />
             <input type="text" placeholder="Search logs..." className="bg-slate-900 pl-8 pr-4 py-1 rounded border border-slate-700 text-sm w-64 text-white focus:border-cyan-500 outline-none" />
          </div>
       </div>
       <table className="w-full text-sm text-left">
          <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
             <tr>
                <th className="p-3">Time</th>
                <th className="p-3">Severity</th>
                <th className="p-3">Message</th>
                <th className="p-3">Source</th>
                <th className="p-3">Action</th>
             </tr>
          </thead>
          <tbody className="divide-y divide-slate-700">
             {notifications.map(n => (
                <tr key={n.id} className="hover:bg-slate-700/20">
                   <td className="p-3 text-slate-400 font-mono">{n.time}</td>
                   <td className="p-3">
                      <span className={`px-2 py-1 rounded text-[10px] uppercase font-bold ${n.type === 'danger' ? 'bg-rose-500 text-white' : n.type === 'warning' ? 'bg-amber-500 text-black' : 'bg-cyan-500 text-black'}`}>
                         {n.type}
                      </span>
                   </td>
                   <td className="p-3 font-medium text-slate-200">{n.msg}</td>
                   <td className="p-3 text-slate-400">System</td>
                   <td className="p-3">
                      <Button size="sm" variant="ghost" onClick={() => acknowledgeAlert(n.id)}>Acknowledge</Button>
                   </td>
                </tr>
             ))}
          </tbody>
       </table>
    </Card>
  );

  const renderQuality = () => (
    <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
       <Card title="Inline Computer Vision Defect Detection">
          <div className="flex gap-4">
             <div className="w-1/2 bg-black rounded border border-slate-700 relative overflow-hidden h-48 flex items-center justify-center">
                <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1624823183488-297072a441df?auto=format&fit=crop&q=80')] bg-cover opacity-30 grayscale"></div>
                <div className="w-24 h-24 border-2 border-rose-500 rounded-full animate-ping absolute top-10 left-10"></div>
                <div className="absolute bottom-2 left-2 bg-rose-600 text-white text-xs px-2 py-1 rounded">Defect Detected: Crack (0.4mm)</div>
             </div>
             <div className="w-1/2 space-y-2">
                <div className="flex justify-between text-sm border-b border-slate-700 pb-2">
                   <span className="text-slate-400">Batch ID</span>
                   <span className="text-white">B-9921</span>
                </div>
                <div className="flex justify-between text-sm border-b border-slate-700 pb-2">
                   <span className="text-slate-400">Sample Size</span>
                   <span className="text-white">500 Units</span>
                </div>
                <div className="flex justify-between text-sm border-b border-slate-700 pb-2">
                   <span className="text-slate-400">Defect Rate</span>
                   <span className="text-rose-400 font-bold">1.2%</span>
                </div>
                <Button variant="danger" className="w-full mt-4" onClick={() => addNotification('warning', 'Production Line PAUSED due to QC Spike')}>
                   <AlertOctagon size={16} /> Auto-Stop Line
                </Button>
             </div>
          </div>
       </Card>

       <Card title="NCR Generation (Non-Conformance Report)">
          <div className="space-y-3">
             <div className="p-3 bg-slate-700/50 rounded border border-slate-600">
                <div className="flex justify-between">
                   <div className="font-bold text-white">NCR #9002</div>
                   <div className="text-xs text-rose-400">Critical</div>
                </div>
                <div className="text-sm text-slate-400 mt-1">Material: Steel Coil (Rust detected)</div>
                <div className="flex gap-2 mt-2">
                   <Button size="sm" variant="secondary">View Photos</Button>
                   <Button size="sm" variant="primary">Email Supplier</Button>
                </div>
             </div>
          </div>
       </Card>
    </div>
  );

  const renderMaintenance = () => (
    <div className="space-y-6">
       <div className="grid grid-cols-1 md:grid-cols-4 gap-4">
          <Card title="Scheduled" noPadding className="items-center justify-center p-4">
             <div className="text-3xl font-bold text-white">4</div>
             <div className="text-xs text-slate-400">Tasks Today</div>
          </Card>
          <Card title="Breakdowns" noPadding className="items-center justify-center p-4 border-rose-500/50">
             <div className="text-3xl font-bold text-rose-500">1</div>
             <div className="text-xs text-rose-400">Active Critical</div>
          </Card>
          <Card title="Technicians" noPadding className="items-center justify-center p-4">
             <div className="text-3xl font-bold text-cyan-400">3/5</div>
             <div className="text-xs text-slate-400">Available</div>
          </Card>
          <Card title="MTTR" noPadding className="items-center justify-center p-4">
             <div className="text-3xl font-bold text-emerald-400">45m</div>
             <div className="text-xs text-slate-400">Avg Repair Time</div>
          </Card>
       </div>

       <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
          <Card title="Predictive Health Monitor (Vibration Analysis)" className="md:col-span-2">
             <ResponsiveContainer width="100%" height={240}>
                <LineChart data={[
                   {t: '09:00', vib: 2.1, limit: 5},
                   {t: '10:00', vib: 2.3, limit: 5},
                   {t: '11:00', vib: 2.8, limit: 5},
                   {t: '12:00', vib: 3.5, limit: 5},
                   {t: '13:00', vib: 4.8, limit: 5}, // Warning
                   {t: '14:00', vib: 5.2, limit: 5}, // Critical
                ]}>
                   <CartesianGrid strokeDasharray="3 3" stroke="#334155" />
                   <XAxis dataKey="t" stroke="#94a3b8" />
                   <YAxis stroke="#94a3b8" />
                   <Tooltip contentStyle={{backgroundColor: '#1e293b', borderColor: '#475569'}} />
                   <ReferenceLine y={5} stroke="red" strokeDasharray="3 3" label="Critical Limit" />
                   <Line type="monotone" dataKey="vib" stroke={COLORS.danger} strokeWidth={2} />
                </LineChart>
             </ResponsiveContainer>
          </Card>
          <Card title="Maintenance Tickets">
             <div className="space-y-3">
                <div className="p-3 bg-rose-900/10 border border-rose-500/50 rounded">
                   <div className="flex justify-between items-start">
                      <div className="font-bold text-rose-400 text-sm">CNC-02 Spindle</div>
                      <span className="text-[10px] bg-rose-500 text-white px-1 rounded">HIGH</span>
                   </div>
                   <div className="text-xs text-slate-400 mt-1">High vibration detected. Possible bearing failure.</div>
                   <div className="mt-2 flex justify-between items-center">
                      <span className="text-[10px] text-slate-500">Tech: Mike T.</span>
                      <Button size="sm" variant="secondary">Details</Button>
                   </div>
                </div>
                <div className="p-3 bg-slate-700/30 border border-slate-600 rounded">
                   <div className="flex justify-between items-start">
                      <div className="font-bold text-slate-200 text-sm">ROBO-01 Filter</div>
                      <span className="text-[10px] bg-cyan-600 text-white px-1 rounded">PM</span>
                   </div>
                   <div className="text-xs text-slate-400 mt-1">Scheduled weekly cleaning.</div>
                   <Button size="sm" variant="ghost" className="w-full mt-2 text-xs">Mark Complete</Button>
                </div>
             </div>
          </Card>
       </div>
    </div>
  );

  const renderOutputFG = () => (
    <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
       <Card title="Finished Goods Stock" className="md:col-span-2">
          <table className="w-full text-sm text-left">
             <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
                <tr>
                   <th className="p-3">FG ID</th>
                   <th className="p-3">SKU Name</th>
                   <th className="p-3">Batch</th>
                   <th className="p-3">Qty</th>
                   <th className="p-3">Status</th>
                   <th className="p-3">Action</th>
                </tr>
             </thead>
             <tbody className="divide-y divide-slate-700">
                {finishedGoods.map(fg => (
                   <tr key={fg.id} className="hover:bg-slate-700/20">
                      <td className="p-3 text-cyan-400 font-mono">{fg.id}</td>
                      <td className="p-3">{fg.sku}</td>
                      <td className="p-3">{fg.batch}</td>
                      <td className="p-3 font-bold text-white">{fg.qty}</td>
                      <td className="p-3"><StatBadge status={fg.status} /></td>
                      <td className="p-3">
                         <Button size="sm" variant="secondary"><Printer size={14}/> Label</Button>
                      </td>
                   </tr>
                ))}
             </tbody>
          </table>
       </Card>
       <Card title="Auto-Packing Station">
          <div className="flex flex-col items-center justify-center h-full p-4 border-2 border-dashed border-slate-600 rounded bg-slate-800/30">
             <Package size={48} className="text-slate-500 mb-4" />
             <div className="text-lg font-bold text-white">Scan Barcode</div>
             <p className="text-sm text-slate-400 text-center mb-4">Place item on scale and scan to generate packing slip.</p>
             <div className="flex w-full gap-2">
                <input type="text" placeholder="Scanning..." disabled className="flex-1 bg-slate-900 border border-slate-700 rounded px-3 py-2 text-sm text-slate-400" />
                <Button variant="primary">Manual</Button>
             </div>
          </div>
       </Card>
    </div>
  );

  const renderDispatch = () => (
     <div className="space-y-6">
        <Card title="Dispatch Control Tower">
           <table className="w-full text-sm text-left">
              <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
                 <tr>
                    <th className="p-3">Order ID</th>
                    <th className="p-3">Customer</th>
                    <th className="p-3">Items</th>
                    <th className="p-3">Status</th>
                    <th className="p-3">Actions</th>
                 </tr>
              </thead>
              <tbody className="divide-y divide-slate-700">
                 {dispatchOrders.map(order => (
                    <tr key={order.id}>
                       <td className="p-3 font-mono text-cyan-400">{order.id}</td>
                       <td className="p-3">{order.customer}</td>
                       <td className="p-3">{order.items}</td>
                       <td className="p-3"><StatBadge status={order.status} /></td>
                       <td className="p-3">
                          {order.status === 'Ready to Ship' && (
                             <Button size="sm" variant="success" onClick={() => generateEWayBill(order.id)}>
                                <FileText size={14} /> Gen E-Way Bill
                             </Button>
                          )}
                          {order.status === 'Shipped' && (
                             <div className="flex items-center gap-1 text-emerald-400 text-xs">
                                <CheckCircle size={14} /> OTP Verified
                             </div>
                          )}
                       </td>
                    </tr>
                 ))}
              </tbody>
           </table>
        </Card>

        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
           <Card title="GPS Logistics Tracker">
              <div className="bg-slate-900 rounded h-48 flex items-center justify-center border border-slate-700 relative">
                 <div className="text-slate-500 text-sm">Map Integration Mockup</div>
                 <MapPin className="text-rose-500 absolute top-1/2 left-1/3 animate-bounce" />
                 <Truck className="text-cyan-500 absolute top-1/2 left-1/2 transition-all duration-1000" />
                 <div className="absolute bottom-2 right-2 bg-slate-800 p-2 rounded text-xs border border-slate-600">
                    <div>TRK-4421</div>
                    <div className="text-emerald-400">On Time (ETA: 2h)</div>
                 </div>
              </div>
           </Card>

           <Card title="Auto-Packing List Generator">
              <div className="flex items-center justify-between p-4 border border-dashed border-slate-600 rounded bg-slate-800/50">
                 <div className="text-center w-full">
                    <Printer className="w-8 h-8 text-slate-400 mx-auto mb-2" />
                    <div className="text-sm text-slate-300">Scan Box Barcode to Print Label</div>
                    <div className="mt-4 flex gap-2 justify-center">
                       <input type="text" placeholder="Scan Barcode..." className="bg-slate-900 border border-slate-600 rounded px-2 py-1 text-sm text-white focus:border-cyan-500 outline-none" />
                       <Button size="sm">Print</Button>
                    </div>
                 </div>
              </div>
           </Card>
        </div>
     </div>
  );

  const renderWorkforce = () => (
     <div className="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <Card title="Shift Attendance & Compliance" className="lg:col-span-1">
           <div className="flex flex-col gap-4">
              <div className="flex justify-between items-center bg-slate-700/30 p-3 rounded">
                 <span className="text-slate-300">Present</span>
                 <span className="text-emerald-400 font-bold">42/45</span>
              </div>
              <div className="flex justify-between items-center bg-slate-700/30 p-3 rounded">
                 <span className="text-slate-300">Safety Violations</span>
                 <span className="text-rose-400 font-bold">0</span>
              </div>
              <div className="flex justify-between items-center bg-slate-700/30 p-3 rounded">
                 <span className="text-slate-300">Overtime (Hrs)</span>
                 <span className="text-amber-400 font-bold">12.5</span>
              </div>
           </div>
        </Card>

        <Card title="AI Skill Matrix & Auto-Assign" className="lg:col-span-2">
           <table className="w-full text-sm text-left">
              <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
                 <tr>
                    <th className="p-3">Operator</th>
                    <th className="p-3">Role</th>
                    <th className="p-3">Top Skill</th>
                    <th className="p-3">Shift</th>
                    <th className="p-3">Assign</th>
                 </tr>
              </thead>
              <tbody className="divide-y divide-slate-700">
                 {SKILL_MATRIX.map((staff, idx) => (
                    <tr key={idx}>
                       <td className="p-3 font-bold text-white">{staff.name}</td>
                       <td className="p-3">{staff.role}</td>
                       <td className="p-3">
                          {Object.entries(staff.skills).sort((a,b) => b[1]-a[1])[0][0]} ({Math.max(...Object.values(staff.skills))}%)
                       </td>
                       <td className="p-3">{staff.shift}</td>
                       <td className="p-3">
                          <Button size="sm" variant="ghost" className="text-cyan-400 border border-cyan-500/30">Assign Task</Button>
                       </td>
                    </tr>
                 ))}
              </tbody>
           </table>
        </Card>
     </div>
  );

  const renderFinance = () => (
    <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
      <Card title="Cost Per SKU Analysis" className="md:col-span-2">
        <ResponsiveContainer width="100%" height={250}>
          <BarChart data={[
            { name: 'AutoPart-X', material: 400, labor: 240, overhead: 100 },
            { name: 'AutoPart-Y', material: 300, labor: 139, overhead: 80 },
            { name: 'Resin-Mold', material: 200, labor: 980, overhead: 120 },
          ]}>
            <CartesianGrid strokeDasharray="3 3" stroke="#334155" />
            <XAxis dataKey="name" stroke="#94a3b8" />
            <YAxis stroke="#94a3b8" />
            <Tooltip contentStyle={{backgroundColor: '#1e293b', borderColor: '#475569'}} />
            <Legend />
            <Bar dataKey="material" stackId="a" fill={COLORS.primary} />
            <Bar dataKey="labor" stackId="a" fill={COLORS.accent} />
            <Bar dataKey="overhead" stackId="a" fill={COLORS.warning} />
          </BarChart>
        </ResponsiveContainer>
      </Card>
      <Card title="Payment Approvals (AI Suggested)">
         <div className="space-y-3">
            {financeData.pendingPayments.map(p => (
              <div key={p.id} className="p-3 border border-slate-700 rounded bg-slate-800/50">
                 <div className="flex justify-between mb-1">
                    <span className="font-bold text-white">{p.vendor}</span>
                    <span className="text-xs text-rose-400">{p.due}</span>
                 </div>
                 <div className="text-2xl font-bold text-emerald-400">${p.amount.toLocaleString()}</div>
                 <div className="mt-2 flex gap-2">
                    {p.status === 'Pending' ? (
                       <Button size="sm" variant="success" className="w-full" onClick={() => approvePayment(p.id)}>Approve</Button>
                    ) : (
                       <div className="w-full text-center text-xs text-emerald-500 font-bold bg-emerald-900/20 py-1 rounded">APPROVED</div>
                    )}
                 </div>
              </div>
            ))}
         </div>
      </Card>
    </div>
  );

  const renderVendorMgmt = () => (
    <div className="space-y-6">
      <Card title="Vendor Performance & Rate Contracts">
        <table className="w-full text-sm text-left">
          <thead className="bg-slate-700/50 text-xs uppercase text-slate-400">
            <tr>
              <th className="p-3">Vendor Name</th>
              <th className="p-3">Rating</th>
              <th className="p-3">Status</th>
              <th className="p-3">YTD Spending</th>
              <th className="p-3">Last Delivery</th>
              <th className="p-3">Action</th>
            </tr>
          </thead>
          <tbody className="divide-y divide-slate-700">
            {vendors.map(v => (
              <tr key={v.id} className="hover:bg-slate-700/20">
                <td className="p-3 font-bold text-white">{v.name}</td>
                <td className="p-3 flex items-center gap-1">
                  {v.rating} <span className="text-amber-400">★</span>
                </td>
                <td className="p-3"><StatBadge status={v.status} /></td>
                <td className="p-3 font-mono">${v.spending.toLocaleString()}</td>
                <td className="p-3 text-slate-400">{v.lastDelivery}</td>
                <td className="p-3">
                  <Button size="sm" variant="secondary">View Contract</Button>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </Card>
    </div>
  );

  const renderCompliance = () => (
    <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
      <Card title="Statutory Audit Logs">
         <div className="space-y-3">
            {COMPLIANCE_LOGS.map(log => (
               <div key={log.id} className="flex items-center justify-between p-3 border-b border-slate-700 last:border-0">
                  <div className="flex items-center gap-3">
                     <div className={`p-2 rounded-full ${log.status === 'Pass' ? 'bg-emerald-500/10 text-emerald-400' : 'bg-rose-500/10 text-rose-400'}`}>
                        {log.status === 'Pass' ? <CheckCircle size={16} /> : <AlertTriangle size={16} />}
                     </div>
                     <div>
                        <div className="text-sm font-bold text-white">{log.type} Check</div>
                        <div className="text-xs text-slate-400">{log.desc}</div>
                     </div>
                  </div>
                  <div className="text-xs text-slate-500">{log.date}</div>
               </div>
            ))}
         </div>
         <Button variant="primary" className="mt-4 w-full"><FileCheck size={16}/> Generate Audit Report</Button>
      </Card>
      <Card title="Digital Document Vault">
         <div className="grid grid-cols-2 gap-4">
            {['Pollution Cert', 'Factory License', 'GST Filings', 'Insurance'].map((doc, i) => (
               <div key={i} className="p-4 bg-slate-700/30 border border-slate-600 rounded flex flex-col items-center justify-center cursor-pointer hover:bg-slate-700 transition-colors">
                  <FileText size={32} className="text-cyan-400 mb-2" />
                  <div className="text-sm text-slate-300">{doc}</div>
                  <div className="text-[10px] text-emerald-400 mt-1">Verified</div>
               </div>
            ))}
         </div>
      </Card>
    </div>
  );

  const renderAIEngine = () => (
    <div className="space-y-6">
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {AI_PREDICTIONS.map((pred, i) => (
           <Card key={i} title={pred.model} className="relative overflow-hidden">
              <div className="absolute top-0 right-0 p-2 opacity-10">
                 <Brain size={64} className="text-white" />
              </div>
              <div className="flex justify-between items-end mb-4">
                 <div>
                    <div className="text-xs text-slate-400">Target</div>
                    <div className="font-bold text-white text-lg">{pred.target}</div>
                 </div>
                 <div className="text-right">
                    <div className="text-3xl font-bold text-cyan-400">{pred.probability}%</div>
                    <div className="text-xs text-slate-500">Confidence</div>
                 </div>
              </div>
              <div className="bg-slate-900/50 p-3 rounded border border-slate-700">
                 <div className="text-[10px] text-slate-400 uppercase tracking-wider mb-1">AI Recommendation</div>
                 <div className="text-sm text-slate-200">{pred.suggestion}</div>
              </div>
              <div className={`mt-3 text-xs font-bold px-2 py-1 inline-block rounded ${pred.impact === 'High' ? 'bg-rose-500/20 text-rose-400' : 'bg-amber-500/20 text-amber-400'}`}>
                 {pred.impact} Impact
              </div>
           </Card>
        ))}
      </div>
      <Card title="Demand vs Supply Prediction Model">
         <ResponsiveContainer width="100%" height={250}>
            <ComposedChart data={[
               {name: 'Wk 1', demand: 4000, supply: 4200, risk: 10},
               {name: 'Wk 2', demand: 3000, supply: 3500, risk: 20},
               {name: 'Wk 3', demand: 5000, supply: 4800, risk: 70}, // Risk
               {name: 'Wk 4', demand: 4500, supply: 4600, risk: 30},
            ]}>
               <CartesianGrid stroke="#334155" />
               <XAxis dataKey="name" stroke="#94a3b8" />
               <YAxis yAxisId="left" stroke="#94a3b8" />
               <YAxis yAxisId="right" orientation="right" stroke="#ef4444" />
               <Tooltip contentStyle={{backgroundColor: '#1e293b', borderColor: '#475569'}} />
               <Legend />
               <Bar yAxisId="left" dataKey="supply" fill={COLORS.primary} barSize={20} />
               <Line yAxisId="left" type="monotone" dataKey="demand" stroke={COLORS.accent} strokeWidth={2} />
               <Area yAxisId="right" type="monotone" dataKey="risk" fill={COLORS.danger} stroke={COLORS.danger} fillOpacity={0.1} />
            </ComposedChart>
         </ResponsiveContainer>
      </Card>
    </div>
  );

  const renderContent = () => {
    switch(activeTab) {
      case 'Overview': return renderOverview();
      case 'Gate Entry': return renderGateEntry();
      case 'GRN & Billing': return renderGRN();
      case 'Stores': return renderStores();
      case 'Material Issue': return renderMaterialIssue();
      case 'Quality Control': return renderQuality();
      case 'Output & FG': return renderOutputFG();
      case 'Maintenance': return renderMaintenance();
      case 'Workforce': return renderWorkforce();
      case 'Dispatch': return renderDispatch();
      case 'Finance': return renderFinance();
      case 'Vendor Mgmt': return renderVendorMgmt();
      case 'Compliance': return renderCompliance();
      case 'AI Engine': return renderAIEngine();
      case 'Live Floor': return renderLiveFloor();
      case 'Alert Center': return renderAlertCenter();
      default: return renderOverview();
    }
  };

  return (
    <div className="flex h-screen bg-slate-950 text-slate-100 font-sans overflow-hidden">
      {/* Sidebar Navigation */}
      <aside className="w-64 bg-slate-900 border-r border-slate-800 flex flex-col shrink-0 transition-all duration-300">
        <div className="p-6 flex items-center gap-3 border-b border-slate-800 shrink-0">
          <div className="w-8 h-8 bg-cyan-600 rounded flex items-center justify-center shrink-0 shadow-[0_0_15px_rgba(6,182,212,0.5)]">
            <Cpu className="text-white w-5 h-5" />
          </div>
          <div className="leading-none">
             <span className="font-bold text-lg tracking-wider block text-white">NUCLEUS</span>
             <span className="text-[10px] text-cyan-400 tracking-widest uppercase">Factory OS v2.0</span>
          </div>
        </div>

        <nav className="flex-1 overflow-y-auto py-4 px-3 space-y-6 custom-scrollbar">
          {navGroups.map((group, idx) => (
            <div key={idx}>
              <div className="px-4 text-[10px] font-bold text-slate-500 uppercase tracking-wider mb-2">{group.title}</div>
              <div className="space-y-1">
                {group.items.map((item) => (
                  <button
                    key={item.name}
                    onClick={() => setActiveTab(item.name)}
                    className={`w-full flex items-center gap-3 px-4 py-2 rounded-lg text-sm transition-all duration-200 group
                      ${activeTab === item.name 
                        ? 'bg-cyan-500/10 text-cyan-400 border border-cyan-500/20 shadow-[0_0_10px_rgba(6,182,212,0.1)]' 
                        : 'text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-transparent'}`}
                  >
                    <item.icon size={16} className={activeTab === item.name ? 'text-cyan-400' : 'text-slate-500 group-hover:text-slate-300'} />
                    <span className="font-medium">{item.name}</span>
                  </button>
                ))}
              </div>
            </div>
          ))}
        </nav>

        <div className="p-4 border-t border-slate-800 shrink-0">
          <div className="bg-slate-800 rounded-lg p-3 flex items-center gap-3">
             <div className="w-8 h-8 rounded bg-gradient-to-br from-indigo-500 to-purple-500 flex items-center justify-center text-xs font-bold">AD</div>
             <div>
                <div className="text-sm font-bold text-white">Admin User</div>
                <div className="text-[10px] text-emerald-400">Online • Plant A</div>
             </div>
          </div>
        </div>
      </aside>

      {/* Main Content Area */}
      <main className="flex-1 flex flex-col overflow-hidden relative bg-slate-950">
        {/* Top Header */}
        <header className="h-16 bg-slate-900/80 backdrop-blur-md border-b border-slate-800 flex items-center justify-between px-6 z-10 shrink-0">
          <div className="flex items-center gap-4">
            <h2 className="text-xl font-semibold text-white tracking-wide flex items-center gap-2">
               {activeTab} 
               {notifications.length > 0 && <span className="flex h-2 w-2 rounded-full bg-rose-500 animate-pulse"></span>}
            </h2>
          </div>

          <div className="flex items-center gap-6">
            <div className="hidden md:flex items-center gap-2 px-3 py-1 bg-slate-800 rounded border border-slate-700">
               <Clock size={14} className="text-cyan-400" />
               <span className="text-sm font-mono text-slate-300">{currentTime}</span>
            </div>
            
            <div className="flex items-center gap-4">
               <button className="relative text-slate-400 hover:text-white transition-colors" onClick={() => setActiveTab('Alert Center')}>
                 <Bell size={20} />
                 {notifications.length > 0 && <span className="absolute -top-1 -right-1 w-4 h-4 bg-rose-500 rounded-full text-[10px] flex items-center justify-center text-white">{notifications.length}</span>}
               </button>
               <button className="text-slate-400 hover:text-white transition-colors">
                 <Settings size={20} />
               </button>
            </div>
          </div>
        </header>

        {/* Dynamic Content */}
        <div className="flex-1 overflow-y-auto p-6 scroll-smooth">
           {renderContent()}
        </div>
      </main>
    </div>
  );
};

export default App;
