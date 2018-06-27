---
title: Bağımlılık özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7398202cc265fbd55b9bf0b5a53367dedcab57b0
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948491"
---
# <a name="dependency-properties"></a>Bağımlılık özellikleri
Bağımlılık özelliği (DP) yerine bir türü değişkeni (alanı), örneğin bir özellik deposu değerini depolar normal bir özelliktir.  
  
 Ekli bağımlılık özelliği "nesneler ve onların kapsayıcılar arasındaki ilişkileri açıklayan özelliklerinin" temsil eden statik alma ve ayarlama yöntemleri olarak Modellenen bağımlılık özelliği türüdür (örn., konumunu bir `Button` nesnenin bir `Panel` kapsayıcı).  
  
 **✓ YAPMAK** stil, Tetikleyiciler, veri bağlama, animasyon, dinamik kaynaklar ve devralma gibi WPF özellikleri desteklemek için özellikler gerekiyorsa bağımlılık özellikleri sağlar.  
  
## <a name="dependency-property-design"></a>Bağımlılık özelliği tasarım  
 **✓ YAPMAK** devralınmalıdır <xref:System.Windows.DependencyObject>, veya bağımlılık özellikleri uygularken kendi alt biri. Türü bir özellik deposu çok verimli bir uygulamasını sağlar ve WPF veri bağlama otomatik olarak destekler.  
  
 **✓ YAPMAK** normal CLR özellik ve bir örneğini depolamak ortak statik salt okunur alan sağlamak <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için.  
  
 **✓ YAPMAK** örnek yöntemleri çağırarak bağımlılık özellikleri uygulamak <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ YAPMAK** özelliğiyle"." özelliğinin adı suffixing tarafından bağımlılık özelliği static alan adı  
  
 **X yok** Ayarla bağımlılık özelliklerinin varsayılan değerlerini açıkça kodda; bunun yerine meta verilerde ayarlayın.  
  
 Özellik varsayılan açıkça ayarlarsanız, bu özellik bir stil gibi bazı örtük yollarla tarafından ayarlanan engelleyebilir.  
  
 **X yok** kodu statik alana erişmek için özellik erişimcisi içinde standart kod dışında koyun.  
  
 Özelliği bir stil gibi örtük bir yöntem ayarlanmışsa, kod stil oluşturma çünkü yürütmesine olmaz statik alanın doğrudan kullanır.  
  
 **X yok** güvenli veri depolamak için bağımlılık özelliklerini kullanın. Hatta özel bağımlılık özellikleri genel olarak erişilebilir.  
  
## <a name="attached-dependency-property-design"></a>Ekli bağımlılık özelliği tasarım  
 Bağımlılık özellikleri önceki bölümde açıklanan bildiri türü iç özelliklerini temsil eder; Örneğin, `Text` özelliği bir özelliğidir `TextButton`, hangi bildirir. Özel türde bir bağımlılık özelliği ekli bağımlılık özelliğidir.  
  
 Ekli özellik klasik bir örneği olan <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği. Düğmenin (değil ızgaranın) sütun konumu özelliğini temsil eder, ancak yalnızca düğme kılavuzunda yer alıyorsa, ve "düğmelere kılavuzları tarafından bağlı olduğu için" ilgili.  
  
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
  
 Erişimciler Get ve Set statik yöntemler tarafından temsil edilen dışında iliştirilmiş bir özellik tanımını çoğunlukla, normal bir bağımlılık özelliğinin, gibi görünür:  
  
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
  
## <a name="dependency-property-validation"></a>Bağımlılık özelliği doğrulama  
 Özellikleri genellikle doğrulama olarak adlandırılan uygulayın. Bir özelliğin değerini değiştirmek için girişiminde bulunulduğunda doğrulama mantığını yürütür.  
  
 Ne yazık ki bağımlılık özellik erişimcisi rasgele doğrulama kodu içeremez. Bunun yerine, bağımlılık özelliği doğrulama mantığını özelliği kayıt sırasında belirtilmesi gerekiyor.  
  
 **X yok** bağımlılık özelliği doğrulama mantığını özelliğin erişimciler yerleştirin. Bunun yerine, bir doğrulama geri çağırma geçirmek `DependencyProperty.Register` yöntemi.  
  
## <a name="dependency-property-change-notifications"></a>Bağımlılık özelliği değişiklik bildirimleri  
 **X yok** bağımlılık özellik erişimcisi değişiklik bildirimi mantığı uygular. Bağımlılık özelliklere sahip bir değişiklik bildirimi geri araması sağlayarak kullanılması gereken bir yerleşik değişiklik bildirimleri özelliği <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Bağımlılık özelliği değeri zorlama  
 Özellik deposu gerçekte değiştirilmeden önce bir özellik ayarlayıcısı verilen değer kurucu tarafından değiştirildiğinde özelliği zorlama gerçekleşir.  
  
 **X yok** bağımlılık özellik erişimcisi zorlama mantığı uygular.  
  
 Bağımlılık özelliklere sahip bir yerleşik zorlama özelliği ve bir zorlama geri sağlayarak kullanılabilir `PropertyMetadata`.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)
