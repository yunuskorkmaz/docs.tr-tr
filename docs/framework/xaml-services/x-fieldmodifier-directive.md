---
title: x:FieldModifier Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484729"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier Yönergesi
Adlandırılmış nesne başvuruları alanları <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varsayılan davranış yerine erişim ile tanımlanabilmesi için xaml derleme davranışını değiştirir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*Public*|<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> Belirtmek<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> için geçirdiğiniz tam dize, kullanılan arka plan kod programlama diline bağlı olarak farklılık gösterir. Bkz. açıklamalar.|  
  
## <a name="dependencies"></a>Bağımlılıkları  
 Bir xaml üretimi her yerde `x:FieldModifier` kullanılıyorsa, bu xaml üretiminin kök öğesi bir [x:Class yönergesi](x-class-directive.md)bildirmelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 `x:FieldModifier`, bir sınıfın veya üyelerinin genel erişim düzeyini bildirmek için uygun değildir. Xaml üretiminin bir parçası olan belirli bir XAML nesnesi işlendiğinde ve bir uygulamanın nesne grafiğinde erişilebilir olabilecek bir nesne haline gelirse, yalnızca XAML işleme davranışı geçerlidir. Varsayılan olarak, bu tür bir nesnenin alan başvurusu Private tutulur, bu da denetim tüketicilerinin doğrudan nesne grafiğini değiştirmesini önler. Bunun yerine, denetim tüketicilerinin, düzen kökü, alt öğe koleksiyonları, adanmış ortak özellikler vb. gibi programlama modelleri tarafından etkinleştirilen standart desenleri kullanarak, nesne grafiğini değiştirmesi beklenmektedir.  
  
 `x:FieldModifier` Özniteliğin değeri programlama diline göre farklılık gösterir ve amacı belirli çerçevelerde farklılık gösterebilir. Kullanılacak dize, her dilin ve <xref:System.CodeDom.Compiler.CodeDomProvider> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>için <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> anlamlarını ve bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.  
  
- İçin C#, atamak <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> için geçirilecek dize olur `public`.  
  
- Microsoft Visual Basic .NET için, atamak <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> için geçirilecek dize olur. `Public`  
  
- /CLI C++için şu anda bir xaml hedefi yok; Bu nedenle, geçirilecek dize tanımsız.  
  
 Ayrıca, (`internal` içinde <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> C# <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , `Friend` Visual Basic), ancak`NotPublic` davranış zaten varsayılan olduğundan belirtilebilir.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>varsayılan davranıştır çünkü XAML 'yi derlenen derlemenin dışındaki kodun XAML tarafından oluşturulan bir öğeye erişmesi gerekir. XAML derleme davranışıyla birlikte WPF güvenlik mimarisi, `x:FieldModifier` özel olarak genel erişime izin verecek şekilde ayarlamadığınız sürece, öğe örneklerini ortak olarak depolayan alanları bildirmeyecektir.  
  
 `x:FieldModifier`yalnızca bir [X:Name Yönergesi](x-name-directive.md) olan öğeler için geçerlidir çünkü bu ad, genel olduktan sonra alana başvurmak için kullanılır.  
  
 Varsayılan olarak, kök öğe için kısmi sınıf geneldir; Ancak, [X:ClassModifier yönergesini](x-classmodifier-directive.md)kullanarak bunu ortak hale getirebilirsiniz. [X:ClassModifier Yönergesi](x-classmodifier-directive.md) , kök öğe sınıfının örneğinin erişim düzeyini de etkiler. Hem hem de `x:Name` `x:FieldModifier` kök öğesine koyabilirsiniz, ancak bu yalnızca kök öğenin genel alan kopyasını, doğru kök öğe sınıfı erişim düzeyiyle birlikte [x:ClassModifier Yönergesi](x-classmodifier-directive.md)tarafından denetlenmeye devam edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için XAML ve Özel Sınıflar](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name Yönergesi](x-name-directive.md)
- [WPF uygulaması oluşturma (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier Yönergesi](x-classmodifier-directive.md)
