---
title: Bağımlılık Özellikleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: bd12d05dbba133503778e6df3cd0e6c3e5689d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709497"
---
# <a name="dependency-properties"></a>Bağımlılık Özellikleri
Bağımlılık özelliği (DP), değerini bir tür değişkeninde (alan) depolamak yerine bir özellik deposunda depolayan normal bir özelliktir.  
  
 İliştirilmiş bir bağımlılık özelliği, nesneler ve kapsayıcıları arasındaki ilişkileri açıklayan "özellikleri" temsil eden, statik get ve set yöntemleri olarak modellenen bir bağımlılık özelliği türüdür (örn. bir `Panel` kapsayıcısında bir `Button` nesnesinin konumu).  
  
 **✓ DO** stil, Tetikleyiciler, veri bağlama, animasyon, dinamik kaynaklar ve devralma gibi WPF özellikleri desteklemek için özellikler gerekiyorsa bağımlılık özellikleri sağlar.  
  
## <a name="dependency-property-design"></a>Bağımlılık özelliği tasarımı  
 **✓ DO** devralınmalıdır <xref:System.Windows.DependencyObject>, veya bağımlılık özellikleri uygularken kendi alt biri. Türü, bir özellik deposunun çok verimli bir uygulamasını sağlar ve otomatik olarak WPF veri bağlamayı destekler.  
  
 **✓ DO** normal CLR özellik ve bir örneğini depolamak ortak statik salt okunur alan sağlamak <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için.  
  
 **✓ DO** örnek yöntemleri çağırarak bağımlılık özellikleri uygulamak <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** özelliğiyle"." özelliğinin adı suffixing tarafından bağımlılık özelliği static alan adı  
  
 **X DO NOT** Ayarla bağımlılık özelliklerinin varsayılan değerlerini açıkça kodda; bunun yerine meta verilerde ayarlayın.  
  
 Özelliği varsayılan olarak ayarlarsanız, bu özelliğin stil gibi bazı örtük yollarla ayarlanmasını engelleyebilirsiniz.  
  
 **X DO NOT** kodu statik alana erişmek için özellik erişimcisi içinde standart kod dışında koyun.  
  
 Stil bir stil gibi örtük yollarla ayarlandıysa, stil statik alanı doğrudan kullandığından bu kod yürütülmez.  
  
 **X DO NOT** güvenli veri depolamak için bağımlılık özelliklerini kullanın. Hatta özel bağımlılık özelliklerine herkese açık bir şekilde erişilebilir.  
  
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
  
 **X DO NOT** bağımlılık özelliği doğrulama mantığını özelliğin erişimciler yerleştirin. Bunun yerine `DependencyProperty.Register` yöntemine bir doğrulama geri çağırması geçirin.  
  
## <a name="dependency-property-change-notifications"></a>Bağımlılık özelliği değişiklik bildirimleri  
 **X DO NOT** bağımlılık özellik erişimcisi değişiklik bildirimi mantığı uygular. Bağımlılık özellikleri, <xref:System.Windows.PropertyMetadata>bir değişiklik bildirimi geri çağırması sağlayarak kullanılması gereken yerleşik bir değişiklik bildirimleri özelliğine sahiptir.  
  
## <a name="dependency-property-value-coercion"></a>Bağımlılık özelliği değer zorlaması  
 Özellik deposu gerçekten değiştirilmeden önce özellik ayarlayıcısına verilen değer ayarlayıcı tarafından değiştirilirse Özellik zorlaması gerçekleşir.  
  
 **X DO NOT** bağımlılık özellik erişimcisi zorlama mantığı uygular.  
  
 Bağımlılık özellikleri yerleşik bir zorlama özelliğine sahiptir ve `PropertyMetadata`bir zorlama geri çağırması sağlayarak kullanılabilir.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)
