---
title: Bağımlılık Özellikleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: e1372b75cb6501f8bc3fec913364e9d80157ad83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741726"
---
# <a name="dependency-properties"></a>Bağımlılık Özellikleri
Bağımlılık özelliği (DP), değerini bir tür değişkeninde (alan) depolamak yerine bir özellik deposunda depolayan normal bir özelliktir.

 İliştirilmiş bir bağımlılık özelliği, nesneler ve kapsayıcıları arasındaki ilişkileri açıklayan "özellikleri" temsil eden, statik get ve set yöntemleri olarak modellenen bir bağımlılık özelliği türüdür (örn. bir `Panel` kapsayıcısında bir `Button` nesnesinin konumu).

 ✔️, stil oluşturma, Tetikleyiciler, veri bağlama, animasyonlar, Dinamik kaynaklar ve devralma gibi WPF özelliklerini desteklemek için özelliklere ihtiyacınız varsa bağımlılık özelliklerini sağlar.

## <a name="dependency-property-design"></a>Bağımlılık özelliği tasarımı
 bağımlılık özelliklerini uygularken <xref:System.Windows.DependencyObject>veya alt türlerinden biri ✔️ devralınır. Türü, bir özellik deposunun çok verimli bir uygulamasını sağlar ve otomatik olarak WPF veri bağlamayı destekler.

 ✔️, her bağımlılık özelliği için bir <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> örneğini depolayan normal bir CLR özelliği ve Public statik salt okunurdur alanı sağlar.

 ✔️, <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>örnek yöntemlerini çağırarak bağımlılık özellikleri uygular.

 ✔️, özelliğin adını "Property" ile düzelterek, bağımlılık özelliği statik alanını adlandırın.

 ❌ doğrudan kodda bağımlılık özelliklerinin varsayılan değerlerini ayarlamayın; Bunun yerine meta verilerde ayarlayın.

 Özelliği varsayılan olarak ayarlarsanız, bu özelliğin stil gibi bazı örtük yollarla ayarlanmasını engelleyebilirsiniz.

 ❌ statik alana erişmek için standart koddan farklı özellik erişimcilerine kod yerleştirmeyin.

 Stil bir stil gibi örtük yollarla ayarlandıysa, stil statik alanı doğrudan kullandığından bu kod yürütülmez.

 ❌, güvenli verileri depolamak için bağımlılık özelliklerini kullanmaz. Hatta özel bağımlılık özelliklerine herkese açık bir şekilde erişilebilir.

## <a name="attached-dependency-property-design"></a>İliştirilmiş bağımlılık özelliği tasarımı
 Önceki bölümde açıklanan bağımlılık özellikleri, bildirim türünün iç özelliklerini temsil eder; Örneğin, `Text` özelliği bir `TextButton`özelliğidir ve bunu bildirir. Özel bir tür bağımlılık özelliği, ekli bağımlılık özelliğidir.

 Ekli özelliğe ait klasik bir örnek <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliktir. Özelliği, düğmenin (Grid 'in) sütun konumunu temsil eder, ancak yalnızca düğmenin bir kılavuzda yer aldığı ve kılavuza göre düğmelere "eklenmiş" olması durumunda geçerlidir.

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 İliştirilmiş bir özelliğin tanımı, erişimcilerinin statik get ve set yöntemlerine göre temsil edildiği durumlar dışında, genellikle normal bağımlılık özelliği gibi görünür:

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a>Bağımlılık özelliği doğrulaması
 Özellikler genellikle doğrulama olarak adlandırılan şeyi uygular. Bir özelliğin değerini değiştirme girişimi yapıldığında doğrulama mantığı yürütülür.

 Ne yazık ki bağımlılık özellik erişimcileri rastgele doğrulama kodu içeremez. Bunun yerine, özellik kaydı sırasında bağımlılık özelliği doğrulama mantığının belirtilmesi gerekir.

 ❌, bağımlılık özelliği doğrulama mantığını özelliğin erişimcilerine yerleştirmeyin. Bunun yerine `DependencyProperty.Register` yöntemine bir doğrulama geri çağırması geçirin.

## <a name="dependency-property-change-notifications"></a>Bağımlılık özelliği değişiklik bildirimleri
 ❌ bağımlılık özelliği erişimcilerinde değişiklik bildirimi mantığını uygulamaz. Bağımlılık özellikleri, <xref:System.Windows.PropertyMetadata>bir değişiklik bildirimi geri çağırması sağlayarak kullanılması gereken yerleşik bir değişiklik bildirimleri özelliğine sahiptir.

## <a name="dependency-property-value-coercion"></a>Bağımlılık özelliği değer zorlaması
 Özellik deposu gerçekten değiştirilmeden önce özellik ayarlayıcısına verilen değer ayarlayıcı tarafından değiştirilirse Özellik zorlaması gerçekleşir.

 ❌ bağımlılık özelliği erişimcilerinde zorlama mantığı uygulamaz.

 Bağımlılık özellikleri yerleşik bir zorlama özelliğine sahiptir ve `PropertyMetadata`bir zorlama geri çağırması sağlayarak kullanılabilir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)
