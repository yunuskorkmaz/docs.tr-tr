---
title: Bağımlılık özellikleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: KrzysztofCwalina
ms.openlocfilehash: b577f42c98cb56fb367cb57a550cb094a8ef105e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145247"
---
# <a name="dependency-properties"></a>Bağımlılık özellikleri
Bağımlılık özelliği (DP) bir tür değişken (alan), örneğin depolamak yerine bir özellik deposu değerini depolayan bir normal bir özelliktir.  
  
 Bir ekli bağımlılık özelliği olarak "Özellikler" nesnelerini ve bunların kapsayıcılar arasındaki ilişkileri tanımlayan temsil eden statik alma ve ayarlama yöntemlerini modellenmiş bağımlılık özelliği türüdür (örneğin, konumunu bir `Button` nesnenin bir `Panel` kapsayıcı).  
  
 **✓ DO** stil, Tetikleyiciler, veri bağlama, animasyon, dinamik kaynaklar ve devralma gibi WPF özellikleri desteklemek için özellikler gerekiyorsa bağımlılık özellikleri sağlar.  
  
## <a name="dependency-property-design"></a>Bağımlılık özelliği tasarımı  
 **✓ DO** devralınmalıdır <xref:System.Windows.DependencyObject>, veya bağımlılık özellikleri uygularken kendi alt biri. Türü bir çok verimli bir özellik deposu sağlar ve otomatik olarak WPF veri bağlamayı destekler.  
  
 **✓ DO** normal CLR özellik ve bir örneğini depolamak ortak statik salt okunur alan sağlamak <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> her bağımlılık özelliği için.  
  
 **✓ DO** örnek yöntemleri çağırarak bağımlılık özellikleri uygulamak <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** özelliğiyle"." özelliğinin adı suffixing tarafından bağımlılık özelliği static alan adı  
  
 **X DO NOT** Ayarla bağımlılık özelliklerinin varsayılan değerlerini açıkça kodda; bunun yerine meta verilerde ayarlayın.  
  
 Açık bir özelliği varsayılan olarak, bu özellik bir stil gibi örtük bazı araçlar tarafından ayarlanan engelleyebilir.  
  
 **X DO NOT** kodu statik alana erişmek için özellik erişimcisi içinde standart kod dışında koyun.  
  
 Özelliği bir stil gibi örtük bir şekilde ayarlanmışsa kod stili uygulanması nedeniyle yürütmesine olmaz statik alan doğrudan kullanır.  
  
 **X DO NOT** güvenli veri depolamak için bağımlılık özelliklerini kullanın. Hatta özel bağımlılık özellikleri genel olarak erişilebilir.  
  
## <a name="attached-dependency-property-design"></a>Ekli bir bağımlılık özelliği tasarımı  
 Bağımlılık özellikleri önceki bölümde açıklanan bildirim türü iç özelliklerini temsil eder; Örneğin, `Text` özelliktir özelliği `TextButton`, hangi bildirir. Özel bağımlılık özelliği ekli bağımlılık özelliği türüdür.  
  
 Ekli özelliği Klasik örneğidir <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği. Düğmenin (değil kılavuz) sütun konumu özelliğini temsil eder, ancak yalnızca düğme kılavuzunda yer alıyorsa, ve "düğmeleri Kılavuzlar tarafından eklenmiş şekilde" ilgili.  
  
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
  
 Erişimciler statik alma ve ayarlama yöntemlerini tarafından temsil edilen dışında ekli özelliği tanımı normal bağımlılık özelliği, çoğunlukla, gibi görünür:  
  
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
 Doğrulama olarak adlandırılan özellikleri genellikle uygulayın. Bir özelliğin değerini değiştirmek için bir deneme yapıldığında Doğrulama mantığı yürütür.  
  
 Ne yazık ki bağımlılık özellik erişimcileri, rastgele bir doğrulama kodu içeremez. Bunun yerine, bağımlılık özelliği Doğrulama mantığı özelliği kayıt sırasında belirtilmesi gerekiyor.  
  
 **X DO NOT** bağımlılık özelliği doğrulama mantığını özelliğin erişimciler yerleştirin. Bunun yerine, doğrulama geri çağırma işlevi için geçirin `DependencyProperty.Register` yöntemi.  
  
## <a name="dependency-property-change-notifications"></a>Bağımlılık özellik değişikliği bildirimleri  
 **X DO NOT** bağımlılık özellik erişimcisi değişiklik bildirimi mantığı uygular. Bağımlılık özelliklerine sahip bir değişiklik bildirimi geri araması için sağlanarak kullanılmalıdır bir yerleşik değişiklik bildirimleri özellik <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Bağımlılık özelliği değer zorlama  
 Özellik zorlama özellik deposu gerçekten değiştirilmeden önce ayarlayıcı tarafından verilen bir özellik ayarlayıcı değer değiştirildiğinde gerçekleşir.  
  
 **X DO NOT** bağımlılık özellik erişimcisi zorlama mantığı uygular.  
  
 Bağımlılık özelliklerine sahip yerleşik zorlama özelliği ve zorlama geri çağırmaya sağlanarak kullanılabilir `PropertyMetadata`.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Ortak Tasarım Desenleri](../../../docs/standard/design-guidelines/common-design-patterns.md)
