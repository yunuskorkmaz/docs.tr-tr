---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614969"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>Ana/ayrıntı senaryosunda ADO verileri görüntülenirken birincil anahtarı değiştirme

#### <a name="details"></a>Ayrıntılar

Bir tür öğe derlediğinizi `Order` ve &quot; &quot; Bu ilişkiyi `Detail` birincil anahtar OrderID aracılığıyla bir tür öğe koleksiyonuyla ilişkili OrderDetails adlı bir ilişkiye &quot; sahip olduğunuzu varsayalım &quot; . WPF uygulamanızda, belirli bir siparişin ayrıntılarına bir liste denetimi bağlayabilirsiniz:

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

DataContext 'in bir olduğu yer `Order` . WPF, özelliğinin değerini alır `OrderDetails` - `Detail` `OrderID` ana öğe ile eşleşen tüm öğelerin D koleksiyonu `OrderID` . Ana öğenin birincil anahtarını değiştirdiğinizde davranış değişikliği ortaya çıkar `OrderID` . ADO, `OrderID` Ayrıntılar koleksiyonundaki etkilenen kayıtların her birini otomatik olarak değiştirir (yani, D koleksiyonuna kopyalanırlar).  Ancak D 'ye ne olur?

- Eski davranış: koleksiyon D temizlendi. Ana *öğe, özelliği* için bir değişiklik bildirimi oluşturmaz `OrderDetails` . Liste kutusu artık boş olan D koleksiyonunu kullanmaya devam eder.
- Yeni davranış: koleksiyon D değiştirilmez. Öğelerinin her biri, özelliği için bir değişiklik bildirimi oluşturur `OrderID` . ListBox, koleksiyonu D 'yi kullanmaya devam eder ve yeni ile ayrıntıları görüntüler `OrderID` . WPF, farklı bir şekilde koleksiyon oluşturarak yeni davranışı uygular: ADO yöntemini <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> `followParent` olarak ayarlanmış bağımsız değişkenle çağırarak `true` .

#### <a name="suggestion"></a>Öneri

Uygulama, aşağıdaki AppContext anahtarını kullanarak yeni davranışı alır.

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

Anahtar, .net `true` 4.7.1 veya sonraki sürümlerini hedefleyen uygulamalar için (eski davranış), `false` .NET 4.7.2 veya üstünü hedefleyen uygulamalar için ise (yeni davranış) olarak varsayılan değeri (eski davranış) olarak ayarlar.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.2       |
| Tür    | Yeniden Hedefleme |
