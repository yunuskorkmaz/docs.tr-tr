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
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053814"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier Yönergesi
Ayrıca sağlandığında xaml derleme davranışını `x:Class` değiştirir. Özellikle, `Public` erişim düzeyine sahip bir kısmi `class` oluşturmak yerine (varsayılan), `NotPublic` belirtilen `x:Class` bir erişim düzeyiyle oluşturulur. Bu davranış, oluşturulan derlemelerdeki sınıfın erişim düzeyini etkiler.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*NotPublic*|<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> Belirtmek<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirilecek tam dize, kullandığınız arka plan kod programlama diline bağlı olarak farklılık gösterir. Bkz. açıklamalar.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 [X:Class](x-class-directive.md) aynı öğe üzerinde de sağlanmalıdır ve bu öğenin bir sayfada kök öğe olması gerekir. Daha fazla bilgi için bkz [ \[. MS-\] xaml Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework xaml Hizmetleri `x:ClassModifier` kullanımındaki değeri programlama diline göre değişir. Kullanılacak dize, her dilin ve <xref:System.CodeDom.Compiler.CodeDomProvider> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>için <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> anlamlarını ve bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.  
  
- İçin C#, atamak <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirilecek dize olur `internal`.  
  
- Microsoft Visual Basic .NET için, atamak <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirilecek dize olur. `Friend`  
  
- /CLI C++için XAML derlemeyi destekleyen bir hedef yok; Bu nedenle, geçirilecek değer belirtilmemiş.  
  
 Ayrıca, (`public` içinde <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> C# <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , `Public` Visual Basic ' de) belirtebilirsiniz; ancak, varsayılan davranış zaten olduğu için, ' de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>  
  
 `private` C#İçindeki gibi eşdeğer Kullanıcı kodu erişim düzeyi kısıtlamalarına sahip diğer değerler, iç içe geçmiş sınıf başvuruları xaml 'de `x:ClassModifier` desteklenmediğinden ve bu nedenle, değiştiricinin aynı etkiye sahip olduğu için ilgili değildir <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> . .  
  
## <a name="security-notes"></a>Güvenlik notları  
 İçinde `x:ClassModifier` bildirildiği gibi erişim düzeyi, hala belirli çerçeveler ve bunların özelliklerine göre yoruma tabidir. WPF, bir paket URI başvurusu aracılığıyla bir WPF `x:ClassModifier` kaynağından `internal`başvuruluyorsa, türü yükleme ve örnek oluşturma özelliklerini içerir. Bu durumun bir sonucu ve diğer çerçeveler tarafından uygulandığı gibi diğerleri, olası tüm örnek oluşturma girişimlerini engellemek için özel olarak `x:ClassModifier` açık değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](x-class-directive.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier Yönergesi](x-fieldmodifier-directive.md)
- [Güvenlik (WPF)](../wpf/security-wpf.md)
- [WPF'den System.Xaml'e Geçirilen Türler](types-migrated-from-wpf-to-system-xaml.md)
