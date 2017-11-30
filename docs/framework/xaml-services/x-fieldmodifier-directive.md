---
title: "x:FieldModifier Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 77745744c0da1e4b4425af6d8e4319faaf524908
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier Yönergesi
Böylece adlandırılmış nesne başvuruları için alanları ile tanımlanmış XAML derleme davranışını değiştiren <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> yerine erişim <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varsayılan davranışı.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*Ortak*|Geçirdiğiniz belirtmek için tam dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> karşı <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , kullanılan arka plan kodu programlama dili bağlı olarak değişir. Açıklamalar bakın.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 XAML üretim kullanıyorsa `x:FieldModifier` herhangi bir yere, o XAML üretim kök öğesinin bildirmelidir bir [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Açıklamalar  
 `x:FieldModifier`bir sınıf veya üyelerine genel erişim düzeyini bildirmek için ilgili değildir. XAML üretim parçası olan belirli bir XAML nesne işlenir ve bir uygulama nesne grafiğinde potansiyel olarak erişilebilen bir nesne olursa yalnızca XAML işleme davranışı için geçerlidir. Varsayılan olarak, böyle bir nesnenin alan başvurusu denetim tüketicileri Nesne grafiği doğrudan değiştirmesini engeller özel tutulur. Bunun yerine, Denetim tüketicileri programlama modelleri tarafından gibi düzeni kök, alt öğe koleksiyonları, ayrılmış ortak özellikleri elde ederek etkinleştirilen standart desenler kullanılarak nesne grafiği değiştirmek için beklenen ve benzeri.  
  
 Değeri `x:FieldModifier` öznitelik programlama diline göre değişir ve amacı içinde belirli çerçeve değişebilir. Her bir dilin nasıl uyguladığını kullanılacak dizesi bağlıdır, <xref:System.CodeDom.Compiler.CodeDomProvider> ve döndürür anlamı tanımlamak için tür dönüştürücüleri <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ve <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, ve bu dil büyük küçük harfe duyarlı olup olmadığını.  
  
-   İçin [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], atamak iletilecek dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olan `public`.  
  
-   İçin [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], atamak iletilecek dizeyi <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> olan `Public`.  
  
-   İçin [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], XAML için hiçbir hedef zaten var; Bu nedenle, iletilecek dizeyi tanımlı değil.  
  
 De belirtebilirsiniz <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` içinde [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` içinde [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) ancak belirten <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> olağandışıdır çünkü `NotPublic` davranışı zaten varsayılan olarak.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>XAML derlenmiş derleme dışına kod XAML oluşturulan öğesine erişmesi gereken sık olduğundan varsayılan davranıştır. WPF XAML derleme davranışı ile birlikte güvenlik mimarisi değil bildirme öğesi örnekleri genel olarak, depolama alanları özellikle ayarlanmadığı sürece `x:FieldModifier` genel erişime izin vermek için.  
  
 `x:FieldModifier`yalnızca öğeleriyle için uygun olan bir [x: Name yönergesi](../../../docs/framework/xaml-services/x-name-directive.md) bu ad alanı ortak sonra başvurmak için kullanıldığından.  
  
 Varsayılan olarak, kök öğe için parçalı sınıf ortak; Ancak, bunu kullanarak ortak olmayan bir duruma getirebilirsiniz [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md). [X: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md) kök öğe sınıfı örneğini erişim düzeyini de etkiler. Her ikisi de koyabilirsiniz `x:Name` ve `x:FieldModifier` kök öğesi, ancak bu yalnızca yapar tarafından denetlenen bir ortak alan kopyasını kök öğe, doğru kök öğe sınıfı erişim düzeyi hala [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML ve WPF için özel sınıflar](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Arka plan kod ve WPF XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x: Name yönergesi](../../../docs/framework/xaml-services/x-name-directive.md)  
 [WPF uygulaması (WPF) oluşturma](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x: ClassModifier yönergesi](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
