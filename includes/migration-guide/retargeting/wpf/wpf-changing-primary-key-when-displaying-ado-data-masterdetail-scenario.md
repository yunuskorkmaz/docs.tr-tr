---
ms.openlocfilehash: 1d9841b9c8989a07820c75ac07940c90e5c0753e
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760909"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF ana/ayrıntı senaryoda ADO veri görüntülerken, birincil bir anahtar değiştirme

|   |   |
|---|---|
|Ayrıntılar|Bir öğe türü ADO koleksiyonunu olduğunu varsayalım <code>Order</code>, adlı bir ilişki ile &quot;OrderDetails&quot; türündeki öğeleri koleksiyonu için ilgili <code>Detail</code> birincil anahtarı aracılığıyla &quot;OrderID&quot;. WPF uygulamanızda belirli bir siparişin ayrıntılarını bir liste denetimini bağlayabilirsiniz:<pre><code class="lang-xml">&lt;ListBox ItemsSource=&quot;{Binding Path=OrderDetails}&quot; &gt;&#13;&#10;</code></pre>DataContext olduğu bir <code>Order</code>. WPF değerini alır <code>OrderDetails</code> özellik - tüm koleksiyonu D <code>Detail</code> ayarlanmış öğeler <code>OrderID</code> eşleşen <code>OrderID</code> ana öğesi. Birincil anahtarı değiştirdiğinizde davranış değişikliği ortaya <code>OrderID</code> ana öğesi. ADO otomatik olarak değiştirir <code>OrderID</code> her etkilenen kayıtların ayrıntıları koleksiyondaki (yani olanları D koleksiyona kopyalandı).  Ancak, D ne olur?<ul><li>Eski davranışı:   Koleksiyon D temizlenir.   Ana öğenin mu <em>değil</em> özelliği için bir değişiklik bildirimi yükseltmek <code>OrderDetails</code>.  Liste kutusu, artık boştur D, koleksiyon kullanmaya devam eder.</li><li>Yeni davranışı:  D değişmeyen koleksiyonudur.   Alt öğelerin her biri için bir değişiklik bildirimi başlatır <code>OrderID</code> özelliği.  ListBox koleksiyonu D kullanmaya devam eder ve yeni ayrıntılarla görüntüler <code>OrderID</code>.</li></ul>WPF, farklı bir yolla D koleksiyonu oluşturarak yeni davranışı uygular: ADO yöntemini çağırarak <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> ile <code>followParent</code> değişkenini <code>true</code>.|
|Öneri|Uygulama, aşağıdaki AppContext anahtarını kullanarak yeni davranış alır.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;&#13;&#10;</code></pre>Varsayılan olarak anahtar <code>true</code> (eski davranışı) .NET 4.7.1'i hedefleyen uygulamalar için veya aşağıda ve için <code>false</code> (yeni davranış) veya üzeri .NET 4.7.2 hedefleyen uygulamalar için.|
|Kapsam|İkincil|
|Sürüm|4.7.2|
|Tür|Yeniden Hedefleme|

