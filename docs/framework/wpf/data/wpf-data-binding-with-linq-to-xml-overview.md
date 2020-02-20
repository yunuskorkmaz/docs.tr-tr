---
title: LINQ to XML ile veri bağlama
ms.date: 10/22/2019
ms.topic: conceptual
ms.openlocfilehash: 65e1524a88f1920c037b2747b0bbe30386951635
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452740"
---
# <a name="overview-of-wpf-data-binding-with-linq-to-xml"></a>LINQ to XML ile WPF veri bağlamaya genel bakış

Bu makalede <xref:System.Xml.Linq> ad alanındaki dinamik veri bağlama özellikleri tanıtılmaktadır. Bu özellikler, Windows Presentation Foundation (WPF) uygulamalarındaki Kullanıcı arabirimi (UI) öğeleri için bir veri kaynağı olarak kullanılabilir. Bu senaryo, <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> ve <xref:System.Xml.Linq.XElement?displayProperty=fullName>özel *dinamik özelliklerine* bağımlıdır.

## <a name="xaml-and-linq-to-xml"></a>XAML ve LINQ to XML

Extensible Application Markup Language (XAML), .NET teknolojilerini desteklemek için Microsoft tarafından oluşturulan bir XML lehçileridir. Kullanıcı arabirimi öğelerini ve olaylar ve veri bağlama gibi ilgili özellikleri temsil etmek için WPF 'de kullanılır. Windows Workflow Foundation, XAML program denetimi (*iş akışları*) gibi program yapısını temsil etmek için kullanılır. XAML, bir teknolojinin bildirim temelli yönlerinin bir programın daha kişiselleştirilmiş davranışını tanımlayan ilgili yordamsal koddan ayrılmasını sağlar.

XAML ve LINQ to XML etkileşime girebileceği iki geniş yol vardır:

- XAML dosyaları iyi biçimlendirilmiş XML olduğundan, LINQ to XML gibi XML teknolojileri aracılığıyla sorgulanabilir ve işlenebilir.

- LINQ to XML sorguları bir veri kaynağını temsil ettiğinden, bu sorgular WPF Kullanıcı arabirimi öğeleri için veri bağlama için bir veri kaynağı olarak kullanılabilir.

Bu belgede İkinci senaryo açıklanmaktadır.

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Windows Presentation Foundation veri bağlama

WPF veri bağlama, bir kullanıcı arabirimi öğesinin özelliklerinden birini bir veri kaynağıyla ilişkilendirebilmesine olanak sağlar. Bunun basit bir örneği, metni Kullanıcı tanımlı bir nesne içinde ortak özelliğin değerini temsil eden bir <xref:System.Windows.Controls.Label>. WPF veri bağlama, aşağıdaki bileşenlere bağımlıdır:

|Bileşen|Açıklama|
|---------------|-----------------|
|Bağlama hedefi|Veri kaynağıyla ilişkilendirilecek Kullanıcı arabirimi öğesi. WPF 'deki görsel öğeler <xref:System.Windows.UIElement> sınıfından türetilir.|
|Target özelliği|Veri bağlama kaynağının değerini yansıtan bağlama hedefinin *bağımlılık özelliği* . Bağımlılık özellikleri, <xref:System.Windows.UIElement> türetilen <xref:System.Windows.DependencyObject> sınıfı tarafından doğrudan desteklenir.|
|Bağlama kaynağı|Sunum için Kullanıcı arabirimi öğesine sağlanan bir veya daha fazla değer için kaynak nesne. WPF, bağlama kaynakları olarak şu türleri otomatik olarak destekler: CLR nesneleri, ADO.NET veri nesneleri, XML verileri (XPath veya LINQ to XML sorgularından) veya başka bir <xref:System.Windows.DependencyObject>.|
|Kaynak yolu|Bağlanacak olan bağlama kaynağının özelliği veya bağlanacak değer kümesi.|

Bağımlılık özelliği, bir UI öğesinin dinamik olarak hesaplanan özelliğini temsil eden WPF 'e özgü bir kavramdır. Örneğin, bağımlılık özellikleri genellikle bir üst öğe tarafından belirtilen varsayılan değerlere veya değerlere sahiptir. Bu özel özellikler, <xref:System.Windows.DependencyProperty> sınıfının örnekleri tarafından desteklenir (standart özelliklerle birlikte alanlar değildir). Daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).

### <a name="dynamic-data-binding-in-wpf"></a>WPF 'de dinamik veri bağlama

Varsayılan olarak, veri bağlama yalnızca hedef UI öğesi başlatıldığında gerçekleşir. Bu, *tek seferlik* bağlama olarak adlandırılır. Çoğu amaçla bu yeterli değildir; Genellikle, bir veri bağlama çözümü, aşağıdakilerden biri kullanılarak değişikliklerin çalışma zamanında dinamik olarak yayılmasını gerektirir:

- *Tek yönlü* bağlama, değişikliklerin bir yandan otomatik olarak yayılmasına neden olur. En yaygın olarak, kaynakta yapılan değişiklikler hedefte yansıtılır, ancak ters işlem bazen yararlı olabilir.

- *İki yönlü* bağlamada, kaynakta yapılan değişiklikler otomatik olarak hedefe yayılır ve hedefteki değişiklikler otomatik olarak kaynağa dağıtılır.

Tek yönlü veya iki yönlü bağlamanın gerçekleşmesi için, kaynağın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayarak veya desteklenen her özellik için bir *PropertyNameChanged* modelini kullanarak bir değişiklik bildirim mekanizması uygulaması gerekir.

WPF 'de veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlama (WPF)](/dotnet/framework/wpf/data/data-binding-wpf).

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>LINQ to XML sınıflarında dinamik özellikler

Çoğu LINQ to XML sınıf uygun WPF dinamik veri kaynakları olarak niteler. En yararlı bilgilerden bazıları yalnızca yöntemler aracılığıyla kullanılabilir, ancak bu sınıflarda Özellikler değişiklik bildirimlerini uygulamaz. WPF veri bağlamayı desteklemek için LINQ to XML, bir dizi *dinamik özellik*kullanıma sunar.

Bu dinamik özellikler, <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflarında mevcut yöntemlerin ve özelliklerin işlevselliğini yineleyen özel çalışma zamanı özellikleridir. Bunlar bu sınıflara yalnızca WPF için dinamik veri kaynakları görevi görmesini sağlamak için eklenmiştir. Bu gereksinimi karşılamak için, tüm bu dinamik özellikler değişiklik bildirimlerini uygular. Bu dinamik özelliklere yönelik ayrıntılı bir başvuru, bir sonraki bölümde verilmiştir [LINQ to XML dinamik özellikler](linq-to-xml-dynamic-properties.md).

> [!NOTE]
> <xref:System.Xml.Linq> ad alanındaki çeşitli sınıflarda bulunan standart ortak özelliklerin birçoğu, tek seferlik veri bağlama için kullanılabilir. Ancak, ne kaynak ne de hedefin bu şema altında dinamik olarak güncelleştirileceğini unutmayın.

### <a name="access-dynamic-properties"></a>Erişim dinamik özellikleri

<xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflarında dinamik özelliklere standart özellikler gibi erişilemez. Örneğin, gibi CLR uyumlu dillerde C#şu olamaz:

- Doğrudan derleme zamanında erişilir. Dinamik özellikler derleyiciye ve Visual Studio IntelliSense 'e görünmez.

- .NET Reflection kullanılarak çalışma zamanında keşfedildi veya erişilir. Çalışma zamanında bile, temel CLR Sense içinde Özellikler değildir.

' C#De, dinamik özelliklere yalnızca <xref:System.ComponentModel> ad alanı tarafından sunulan tesislerde çalışma zamanında erişilebilir.

Buna karşılık, bir XML kaynak dinamik özelliklerine aşağıdaki biçimde doğrudan bir gösterim aracılığıyla erişilebilir:

```xml
<object>.<dynamic-property>
```

Bu iki sınıf için dinamik özellikler, doğrudan kullanılabilecek bir değere çözümlenmez ya da sonuç değerini ya da değerleri toplamayı elde etmek için bir dizinle birlikte sağlanması gereken bir dizin oluşturucudur. İkinci sözdizimi şu biçimdedir:

```xml
<object>.<dynamic-property>[<index-value>]
```

Daha fazla bilgi için bkz. [dinamik özellikler LINQ to XML](linq-to-xml-dynamic-properties.md).

WPF dinamik bağlamayı uygulamak için dinamik özellikler, <xref:System.Windows.Data> ad alanı tarafından sunulan tesislerle birlikte kullanılır, bu da özellikle <xref:System.Windows.Data.Binding> sınıfıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML ile WPF Verilerini Bağlama](wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ to XML Dinamik Özellikleri](linq-to-xml-dynamic-properties.md)
- [WPF'de XAML](../advanced/xaml-in-wpf.md)
- [Veri bağlama (WPF)](/dotnet/framework/wpf/data/data-binding-wpf)
- [Iş akışı Işaretlemesini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms735921(v=vs.90))
