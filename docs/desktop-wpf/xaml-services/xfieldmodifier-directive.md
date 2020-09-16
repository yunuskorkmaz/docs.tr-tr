---
title: x:FieldModifier Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554481"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier Yönergesi
Adlandırılmış nesne başvuruları alanları <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> varsayılan davranış yerine erişim ile tanımlanabilmesi IÇIN xaml derleme davranışını değiştirir <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> .

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*Geneldir*|Belirtmek için geçirdiğiniz tam dize <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullanılan arka plan kod programlama diline bağlı olarak farklılık gösterir. Bkz. açıklamalar.|

## <a name="dependencies"></a>Bağımlılıklar

 Bir XAML üretimi `x:FieldModifier` her yerde kullanılıyorsa, bu xaml üretiminin kök öğesi bir [X:Class yönergesi](xclass-directive.md)bildirmelidir.

## <a name="remarks"></a>Açıklamalar

`x:FieldModifier` , bir sınıfın veya üyelerinin genel erişim düzeyini bildirmek için uygun değildir. Xaml üretiminin bir parçası olan belirli bir XAML nesnesi işlendiğinde ve bir uygulamanın nesne grafiğinde erişilebilir olabilecek bir nesne haline gelirse, yalnızca XAML işleme davranışı geçerlidir. Varsayılan olarak, bu tür bir nesnenin alan başvurusu Private tutulur, bu da denetim tüketicilerinin doğrudan nesne grafiğini değiştirmesini önler. Bunun yerine, denetim tüketicilerinin, düzen kökü, alt öğe koleksiyonları, adanmış ortak özellikler vb. gibi programlama modelleri tarafından etkinleştirilen standart desenleri kullanarak, nesne grafiğini değiştirmesi beklenmektedir.

`x:FieldModifier`Özniteliğin değeri programlama diline göre farklılık gösterir ve amacı belirli çerçevelerde farklılık gösterebilir. Kullanılacak dize, her dilin <xref:System.CodeDom.Compiler.CodeDomProvider> ve için anlamlarını ve <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> bu dilin büyük/küçük harfe duyarlı olup olmadığını tanımlamak için döndürdüğü tür Dönüştürücülerine bağlıdır.

- C# için, atamak için geçirilecek dize <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olur `public` .

- Microsoft Visual Basic .NET için, atamak için geçirilecek dize <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olur `Public` .

- C++/CLı için şu anda XAML için hiçbir hedef yok; Bu nedenle, geçirilecek dize tanımsız.

Ayrıca, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ( `internal` C# ' de `Friend` Visual Basic), ancak <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> davranış zaten varsayılan olduğundan, olağan dışı `NotPublic` olarak belirtmek de belirtebilirsiniz.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varsayılan davranıştır çünkü XAML 'yi derlenen derlemenin dışındaki kodun XAML tarafından oluşturulan bir öğeye erişmesi gerekir. XAML derleme davranışıyla birlikte WPF güvenlik mimarisi, özel olarak `x:FieldModifier` genel erişime izin verecek şekilde ayarlamadığınız sürece, öğe örneklerini ortak olarak depolayan alanları bildirmeyecektir.

`x:FieldModifier` yalnızca bir [X:Name Yönergesi](xname-directive.md) olan öğeler için geçerlidir çünkü bu ad, genel olduktan sonra alana başvurmak için kullanılır.

Varsayılan olarak, kök öğe için kısmi sınıf geneldir; Ancak, [X:ClassModifier yönergesini](xclassmodifier-directive.md)kullanarak bunu ortak hale getirebilirsiniz. [X:ClassModifier Yönergesi](xclassmodifier-directive.md) , kök öğe sınıfının örneğinin erişim düzeyini de etkiler. Hem hem de `x:Name` `x:FieldModifier` kök öğesine koyabilirsiniz, ancak bu yalnızca kök öğenin genel alan kopyasını, doğru kök öğe sınıfı erişim düzeyiyle birlikte [X:ClassModifier Yönergesi](xclassmodifier-directive.md)tarafından denetlenmeye devam edebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF için XAML ve Özel Sınıflar](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [Arka Plan Kod ve WPF İçindeki XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:Name Yönergesi](xname-directive.md)
- [WPF Uygulaması Oluşturma (WPF)](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)
- [x:ClassModifier Yönergesi](xclassmodifier-directive.md)
