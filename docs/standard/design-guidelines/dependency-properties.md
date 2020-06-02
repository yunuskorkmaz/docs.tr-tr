---
title: Bağımlılık Özellikleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 476ef1bb1ac5ec1f551979c64a41cbae55c554bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280263"
---
# <a name="dependency-properties"></a>Bağımlılık Özellikleri
Bağımlılık özelliği (DP), değerini bir tür değişkeninde (alan) depolamak yerine bir özellik deposunda depolayan normal bir özelliktir.

 İliştirilmiş bir bağımlılık özelliği, nesneler ve kapsayıcıları arasındaki ilişkileri açıklayan "özellikleri" temsil eden, statik get ve set yöntemleri olarak modellenen bir bağımlılık özelliği türüdür (örn. `Button` bir kapsayıcı üzerindeki nesnenin konumu `Panel` ).

 ✔️, stil oluşturma, Tetikleyiciler, veri bağlama, animasyonlar, Dinamik kaynaklar ve devralma gibi WPF özelliklerini desteklemek için özelliklere ihtiyacınız varsa bağımlılık özelliklerini sağlar.

## <a name="dependency-property-design"></a>Bağımlılık özelliği tasarımı
 <xref:System.Windows.DependencyObject>bağımlılık özelliklerini uygularken ✔️ veya alt türlerinden birini devralma. Türü, bir özellik deposunun çok verimli bir uygulamasını sağlar ve otomatik olarak WPF veri bağlamayı destekler.

 ✔️, <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için bir örneğini depolayan normal BIR CLR özelliği ve ortak statik salt okunurdur.

 ✔️, örnek yöntemlerini ve yöntemini çağırarak bağımlılık özelliklerini <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> uygulama <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> .

 ✔️, özelliğin adını "Property" ile düzelterek, bağımlılık özelliği statik alanını adlandırın.

 ❌Doğrudan kodda bağımlılık özelliklerinin varsayılan değerlerini ayarlamayın; Bunun yerine meta verilerde ayarlayın.

 Özelliği varsayılan olarak ayarlarsanız, bu özelliğin stil gibi bazı örtük yollarla ayarlanmasını engelleyebilirsiniz.

 ❌Statik alana erişmek için standart kod dışındaki özellik erişimcilerine kod yerleştirmeyin.

 Stil bir stil gibi örtük yollarla ayarlandıysa, stil statik alanı doğrudan kullandığından bu kod yürütülmez.

 ❌Güvenli verileri depolamak için bağımlılık özelliklerini kullanmayın. Hatta özel bağımlılık özelliklerine herkese açık bir şekilde erişilebilir.

## <a name="attached-dependency-property-design"></a>İliştirilmiş bağımlılık özelliği tasarımı
 Önceki bölümde açıklanan bağımlılık özellikleri, bildirim türünün iç özelliklerini temsil eder; Örneğin, `Text` özelliği `TextButton` onu bildiren bir özelliğidir. Özel bir tür bağımlılık özelliği, ekli bağımlılık özelliğidir.

 Ekli özelliğe klasik bir örnek, <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliktir. Özelliği, düğmenin (Grid 'in) sütun konumunu temsil eder, ancak yalnızca düğmenin bir kılavuzda yer aldığı ve kılavuza göre düğmelere "eklenmiş" olması durumunda geçerlidir.

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

 ❌Bağımlılık özelliği doğrulama mantığını özelliğin erişimcilerine yerleştirmeyin. Bunun yerine yöntemine bir doğrulama geri çağırması geçirin `DependencyProperty.Register` .

## <a name="dependency-property-change-notifications"></a>Bağımlılık özelliği değişiklik bildirimleri
 ❌Bağımlılık özelliği erişimcilerinde değişiklik bildirimi mantığını uygulamayın. Bağımlılık özellikleri, için bir değişiklik bildirimi geri çağırması sağlayarak kullanılması gereken yerleşik bir değişiklik bildirimleri özelliğine sahiptir <xref:System.Windows.PropertyMetadata> .

## <a name="dependency-property-value-coercion"></a>Bağımlılık özelliği değer zorlaması
 Özellik deposu gerçekten değiştirilmeden önce özellik ayarlayıcısına verilen değer ayarlayıcı tarafından değiştirilirse Özellik zorlaması gerçekleşir.

 ❌Bağımlılık özelliği erişimcilerinde zorlama mantığı uygulamayın.

 Bağımlılık özellikleri yerleşik bir zorlama özelliğine sahiptir ve ' a bir zorlama geri çağırması sağlanarak kullanılabilir `PropertyMetadata` .

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Ortak tasarım desenleri](common-design-patterns.md)
