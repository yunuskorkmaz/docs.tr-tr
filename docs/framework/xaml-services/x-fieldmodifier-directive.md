---
title: x:FieldModifier Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 0ce219ca5477c5714225cfc86fe29334bea30a88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611208"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier Yönergesi
Adlandırılmış nesne başvuruları için alanları ile tanımlanan şekilde XAML derlemesi davranışı değiştirir <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> yerine erişim <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varsayılan davranışı.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*Public*|Geçirdiğiniz belirtmek için tam dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> karşı <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullanılan arka plan kod programlama diline bağlı olarak değişir. Açıklamalara bakın.|  
  
## <a name="dependencies"></a>Bağımlılıkları  
 XAML üretim kullanıyorsa `x:FieldModifier` her yerden bu XAML üretim kök öğesi bildirmelidir bir [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Açıklamalar  
 `x:FieldModifier` bir sınıf veya üyelerinin genel erişim düzeyi bildirmek için geçerli değildir. XAML üretim parçası olan özel bir XAML nesne işlenir ve bir uygulamanın nesne grafiğinde potansiyel olarak erişilebilen bir nesne haline gelir oluşturulurken yalnızca XAML işleme davranışını için geçerlidir. Varsayılan olarak, bu tür bir nesne için alan başvurusu denetimi tüketiciler Nesne grafiğini doğrudan değiştirmesini engeller özel tutulur. Bunun yerine, Denetim tüketicileri programlama modelleriyle gibi Düzen kök veya alt öğe koleksiyonlarını, adanmış ortak özellikler, elde ederek etkinleştirilen standart desenler kullanılarak nesne grafını değiştirin beklenir ve benzeri.  
  
 Değeri `x:FieldModifier` öznitelik programlama diline göre değişir ve belirli çerçeveleri amacı farklılık gösterebilir. Her bir dilin nasıl uyguladığını kullanılacak dize bağlıdır, <xref:System.CodeDom.Compiler.CodeDomProvider> ve döndürür anlamı tanımlamak için tür dönüştürücüleri <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, ve bu dilin büyük küçük harfe duyarlı olup olmadığını.  
  
-   C#, belirlemek üzere iletilecek dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olduğu `public`.  
  
-   Microsoft Visual Basic .NET, atamak için geçirilecek dize için <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olduğu `Public`.  
  
-   İçin [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], XAML için hiçbir hedef zaten var; Bu nedenle, dize geçirilecek tanımsızdır.  
  
 Belirtebilirsiniz <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` içinde C#, `Friend` Visual Basic'te) ancak belirten <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olağan dışı çünkü `NotPublic` varsayılan davranışı olduğundan.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> kod derlenmiş XAML derleme dışından XAML oluşturulmuş bir öğe erişmesi seyrek olduğundan varsayılan davranıştır. WPF XAML derlemesi davranışı birlikte güvenlik mimarisi değil bildirmek öğesi örnekleri genel, depolama alanları, özel olarak ayarlamadığınız sürece `x:FieldModifier` genel erişime izin vermek için.  
  
 `x:FieldModifier` yalnızca öğeler için uygun olan bir [x: Name yönergesi](../../../docs/framework/xaml-services/x-name-directive.md) bu ad genel sonra alanına başvurmak için kullanıldığından.  
  
 Varsayılan olarak, kısmi sınıf kök öğe için genel; Ancak, bunu kullanarak özel bir duruma getirebilirsiniz [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md). [X: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md) kök öğe sınıfı örneğini erişim düzeyini de etkiler. Her ikisi de koyabilirsiniz `x:Name` ve `x:FieldModifier` kök öğesi, ancak bu yalnızca yapar tarafından denetlenen bir ortak alan kopyasını kök öğesiyle true kök öğe sınıfı erişim düzeyi hala [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WPF için XAML ve Özel Sınıflar](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name Yönergesi](../../../docs/framework/xaml-services/x-name-directive.md)
- [WPF uygulaması (WPF) oluşturma](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier Yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
