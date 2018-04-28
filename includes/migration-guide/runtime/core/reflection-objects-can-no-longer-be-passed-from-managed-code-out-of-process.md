### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Yansıma nesneler artık yönetilen koddan işlem dışı DCOM istemcilere geçirilebilir

|   |   |
|---|---|
|Ayrıntılar|Yansıma nesneleri işlem dışı DCOM istemcilere artık yönetilen koddan geçirilebilir. Aşağıdaki türlerden etkilenir:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (ve de dahil olmak üzere kendi türetilmiş türler <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, ve <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Çağrılar <code>IMarshal</code> dönüş nesnesinin <code>E_NOINTERFACE</code>.|
|Öneri|Yansıma olmayan nesneler ile çalışmak için hazırlama kodunu güncelleştirin|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Çalışma zamanı|

