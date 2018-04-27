### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Bazı iş akışı sürükle ve bırak API artık kullanılmıyor

|   |   |
|---|---|
|Ayrıntılar|Bu iş akışı sürükle ve bırak API artık kullanılmıyor ve uygulama karşı 4.5 yeniden oluşturulursa derleyici uyarıları neden olur.|
|Öneri|Yeni <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> birden fazla nesne işlemleriyle destekler API'lerini bunun yerine kullanılmalıdır. Alternatif olarak, derleme uyarıları gizlenebilir veya eski bir derleyici kullanılarak önlenebilir. API'ler hala desteklenmektedir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

