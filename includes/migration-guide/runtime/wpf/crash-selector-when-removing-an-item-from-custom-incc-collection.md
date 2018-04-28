### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Seçici içinde bir öğe özel bir INCC koleksiyondan kaldırırken kilitlenme

|   |   |
|---|---|
|Ayrıntılar|Bir <code>T:System.InvalidOperationException</code> aşağıdaki senaryolarda oluşabilir:<ul><li>ItemsSource için bir <code>T:System.Windows.Controls.Primitives.Selector</code> bir koleksiyondur, özel bir uygulama <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Seçili öğeyi koleksiyondan kaldırılır.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Sahip <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (bir bilinmeyen konumu belirtir).</li></ul>Özel durum çağrı yığını System.Windows.Threading.Dispatcher.VerifyAccess() System.Windows.DependencyObject.GetValue (DependencyProperty dp) System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject adresindeki adresindeki başlar öğesi) uygulama, birden fazla dağıtıcı iş parçacığı içeriyorsa, bu özel durumun .net 4.5 ortaya çıkabilir. .NET 4.7 tek bir dağıtıcı iş parçacığı ile uygulamalarında özel durumu oluşabilir. .Net 4.7.1 sorun düzeltilmiştir.|
|Öneri|.Net 4.7.1'ye yükseltin.|
|Kapsam|Küçük|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

