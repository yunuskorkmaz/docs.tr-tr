### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a>4.0 ve 4.5 arasındaki Regex.CompileToAssembly sonları ile derlenmiş derlemeler

|   |   |
|---|---|
|Ayrıntılar|Bütünleştirilmiş koda derlenmiş bir normal ifade .NET Framework 4.5 ancak hedef .NET Framework 4 ile oluşturulursa, derleme bir sistemde, .NET Framework 4 yüklü, normal ifadelerden biri kullanmaya çalışıyor bir özel durum oluşturur.|
|Öneri|Bu sorunu geçici olarak çözmek için aşağıdakilerden birini yapabilirsiniz:<ul><li>.NET Framework 4 Normal ifadelerle içeren derleme.</li><li>Yorumlanan bir normal ifade kullanın.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|

