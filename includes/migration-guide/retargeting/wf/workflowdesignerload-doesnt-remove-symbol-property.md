### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>Sembol özellik WorkflowDesigner.Load kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 5'iş akışı Tasarımcısı'nı ve yeniden barındırılan 3.5 akışıyla yüklenirken hedeflerken <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemi, bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> iş akışı kaydedilirken atılır.|
|Öneri|Bu hata yalnızca .NET Framework 4.5, geçici ayarlayarak çalışılabilecek biçimde iş akışı Tasarımcısı'nda hedeflerken bildirimleri <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> 4.0 .NET Framework.Alternatively kullanarak sorunu kalmayabilir <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> iş akışını yüklemek için yöntemi yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

