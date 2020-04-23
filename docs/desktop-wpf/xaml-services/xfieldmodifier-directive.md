---
title: x:FieldModifier Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071530"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier Yönergesi
XAML derleme davranışını, adlandırılmış nesne başvurularıiçin alanların <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varsayılan davranış yerine erişimle tanımlanması için değiştirir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*Kamu*|Karşı belirtmek <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> için geçtiğiniz <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> tam dize, kullanılan kod arkası programlama diline bağlı olarak değişir. Bkz. Açıklamalar.|

## <a name="dependencies"></a>Bağımlılıklar

 Bir XAML üretimi `x:FieldModifier` herhangi bir yerde kullanıyorsa, bu XAML üretiminin kök öğesi [x:Sınıf Yönergesi](xclass-directive.md)bildirmelidir.

## <a name="remarks"></a>Açıklamalar

`x:FieldModifier`bir sınıfın veya üyelerinin genel erişim düzeyini bildirmekle ilgili değildir. Yalnızca XAML üretiminin bir parçası olan belirli bir XAML nesnesi işlendiğinde ve bir uygulamanın nesne grafiğinde erişilebilen bir nesne haline geldiğinde XAML işleme davranışı için geçerlidir. Varsayılan olarak, böyle bir nesneiçin alan başvurusu gizli tutulur ve bu da denetim tüketicilerinin nesne grafiğini doğrudan değiştirmesini engeller. Bunun yerine, denetim tüketicilerinin düzen kökünü, alt öğe koleksiyonlarını, özel ortak özellikleri ve benzeri gibi programlama modelleri tarafından etkinleştirilen standart desenleri kullanarak nesne grafiğini değiştirmeleri beklenir.

Öznitelik değeri `x:FieldModifier` programlama diline göre değişir ve amacı belirli çerçevelerde değişebilir. Kullanılacak dize, her dilin kendi <xref:System.CodeDom.Compiler.CodeDomProvider> sini nasıl uyguladığına ve anlamları tanımlamak <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>için döndürdüğü tür dönüştürücülerine ve bu dilin büyük/küçük harf duyarlı olup olmadığına bağlıdır.

- C# için, belirtmek <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> için geçmek `public`için dize.

- Microsoft Visual Basic .NET için, belirtmek <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public`için geçmek için dize.

- C++/CLI için şu anda XAML için hedef yok; bu nedenle, geçmek için dize tanımsız.

Ayrıca <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `internal` (C#, Visual `Friend` Basic'te) belirtebilirsiniz, ancak `NotPublic` davranış zaten varsayılan olduğundan belirtinebilirsiniz. <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>XAML'yi derleyen derleme dışındaki kodun XAML tarafından oluşturulan bir öğeye erişmesi gerektiğinden varsayılan davranıştır. WPF güvenlik mimarisi, XAML derleme davranışıyla birlikte, genel erişime izin verecek `x:FieldModifier` şekilde özel olarak ayarlamadığınız sürece, öğe örneklerini herkese açık olarak depolayan alanları beyan etmez.

`x:FieldModifier`yalnızca [x:Name Yönergesi](xname-directive.md) olan öğeler için alakalıdır, çünkü bu ad alana genel olarak başvuru yapmak için kullanılır.

Varsayılan olarak, kök öğeiçin kısmi sınıf ortaktır; ancak [x:ClassModifier](xclassmodifier-directive.md)Yönergesi'ni kullanarak herkese açık olmayan hale getirebilirsiniz. [x:ClassModifier Yönergesi,](xclassmodifier-directive.md) kök öğe sınıfının örnek erişim düzeyini de etkiler. Hem de `x:Name` `x:FieldModifier` kök öğesi üzerine koyabilirsiniz, ancak bu sadece gerçek kök öğesi sınıf erişim düzeyi hala x tarafından kontrol ile kök öğesinin ortak bir alan kopyasını [yapar:ClassModifier Yönergesi](xclassmodifier-directive.md).

## <a name="see-also"></a>Ayrıca bkz.

- [WPF için XAML ve Özel Sınıflar](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Arka Plan Kod ve WPF İçindeki XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name Yönergesi](xname-directive.md)
- [WPF Uygulaması Oluşturma (WPF)](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier Yönergesi](xclassmodifier-directive.md)
