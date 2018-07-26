### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>Sembol özellik WorkflowDesigner.Load kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 5'iş akışı Tasarımcısı ve 3.5 yeniden barındırılan iş akışı ile yüklenirken hedeflenirken <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemi, bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> kaydedilirken iş akışı oluşturulur.|
|Öneri|Bu hata yalnızca, geçici olarak ayarlayarak çalışılabilmesi için .NET Framework 4.5 iş akışı Tasarımcısı'nda hedeflenirken bildirimlerini <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> kullanarak sorunu 4.0 .NET Framework.Alternatively kalmayabilir <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> yük iş akışı için yöntemi yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Kapsam|Büyük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

