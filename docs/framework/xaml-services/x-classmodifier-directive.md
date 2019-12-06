---
title: x:ClassModifier Yönergesi
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837239"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier Yönergesi
`x:Class` de sağlandığında XAML derleme davranışını değiştirir. Özellikle, `Public` erişim düzeyine sahip (varsayılan) bir kısmi `class` oluşturmak yerine, belirtilen `x:Class` `NotPublic` erişim düzeyiyle oluşturulur. Bu davranış, oluşturulan derlemelerdeki sınıfın erişim düzeyini etkiler.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*NotPublic*|<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> belirtmek için geçirilecek tam dize, kullandığınız kod arkasındaki programlama diline bağlı olarak değişir. Bkz. açıklamalar.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 [X:Class](x-class-directive.md) aynı öğe üzerinde de sağlanmalıdır ve bu öğenin bir sayfada kök öğe olması gerekir. Daha fazla bilgi için bkz. [\[MS-XAML\] Bölüm 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML Hizmetleri kullanımındaki `x:ClassModifier` değeri programlama diline göre farklılık gösterir. Kullanılacak dize, her dilin <xref:System.CodeDom.Compiler.CodeDomProvider> nasıl uyguladığı ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>anlamlarını ve bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.  
  
- İçin C#, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> belirlemek için geçirilecek dize `internal`.  
  
- Microsoft Visual Basic .NET için, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> belirlemek için geçirilecek dize `Friend`.  
  
- /CLI C++için XAML derlemeyi destekleyen bir hedef yok; Bu nedenle, geçirilecek değer belirtilmemiş.  
  
 Ayrıca C#, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> de belirtebilirsiniz (`public`, Visual Basic içinde `Public`); Ancak, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zaten varsayılan davranış olduğu için <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> belirtme işlemi seyrek yapılır.  
  
 İçinde C#`private` gibi eşdeğer Kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer değerler, XAML 'de iç içe geçmiş sınıf başvuruları desteklenmediğinden `x:ClassModifier` için uygun değildir ve bu nedenle <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> değiştiricisi aynı etkiye sahiptir.  
  
## <a name="security-notes"></a>Güvenlik notları  
 `x:ClassModifier` içinde bildirildiği gibi erişim düzeyi, hala belirli çerçeveler ve bunların özelliklerine göre yoruma tabidir. WPF, bir paket URI başvurusu aracılığıyla bir WPF kaynağından başvuruluyorsa, `x:ClassModifier` `internal`olan türleri yükleme ve oluşturma özelliklerini içerir. Bu durumun bir sonucu ve diğer çerçeveler tarafından uygulandığı gibi diğerleri, olası tüm örnek oluşturma girişimlerini engellemek için yalnızca `x:ClassModifier` güvenmeyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier Yönergesi](x-fieldmodifier-directive.md)
- [Güvenlik (WPF)](../wpf/security-wpf.md)
- [WPF'den System.Xaml'e Geçirilen Türler](types-migrated-from-wpf-to-system-xaml.md)
