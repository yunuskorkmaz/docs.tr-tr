---
title: x:FactoryMethod Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071537"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod Yönergesi
Bir XAML işlemcinin bir nesneyi destek türünü çözdükten sonra başlatmayı kullanmak için kullanması gereken bir oluşturucu dışında bir yöntem belirtir.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML Öznitelik Kullanımı, x:Bağımsız Değişkenler yok  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML Öznitelik Kullanımı, x:Element(ler) olarak bağımsız değişkenler  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`methodname`|XAML işlemcilerinin çağırdığı bir yöntemin dize yöntemi adı, 'da `object`belirtilen örneği başlatmayı. Bkz. Açıklamalar.|  
|`oneOrMoreObjectElements`|Fabrika yöntemi parametrelerini belirten nesneler için bir veya daha fazla nesne öğesi. Düzen önemlidir; bağımsız değişkenlerin fabrika yöntemine geçirilme sırasını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Örnek `methodname` bir yöntemse, nitelikli olamaz.  
  
 Fabrika yöntemleri olarak statik yöntemler desteklenir. Statik `methodname` bir yöntem `methodname` ise, statik `typeName.methodName` fabrika `typeName` yöntemini tanımlayan sınıfı adlandırır bir kombinasyon olarak sağlanır. `typeName`eşlenen xmlns bir tür atıfta varsa önek nitelikli olabilir. `typeName`daha farklı bir `typeof(object)`tür olabilir.  
  
 Fabrika yöntemi, ilgili nesne öğeöğesini destekleyen türün genel olarak bildirilen bir yöntemi olmalıdır.  
  
 Fabrika yöntemi, ilgili nesneye atayabilen bir örneği döndürmelidir. Fabrika yöntemleri asla null dönmelidir.  
  
 `x:Arguments`fabrika yöntemlerinin imzaları için en iyi maç prensibine göre çalışır. Eşleştirme önce parametre sayısını değerlendirir. Bir parametre sayısı için birden fazla olası eşleşme varsa, parametre türü değerlendirilir ve en iyi eşleşme belirlenir. Bu değerlendirme aşamasından sonra hala belirsizlik varsa, XAML işlemci davranışı tanımsızdır.  
  
 Yönerge biçimlendirmesi `x:FactoryMethod` içeren nesne öğe öğesinin türüne başvurmadığından, öğe kullanımı tipik anlamda özellik öğesi kullanımı değildir. Öğe kullanımının öznitelik kullanımından daha az yaygın olması beklenir. `x:Arguments`(öznitelik veya eleman kullanımı) öğe `x:FactoryMethod` kullanımıyla birlikte kullanılabilir, ancak bu özellikle Kullanım bölümlerinde gösterilmez.  
  
 `x:FactoryMethod`bir öğe diğer özellik öğeleri önce gerekir, `x:Arguments` herhangi bir da elements olarak sağlanan önce ve herhangi bir içerik / iç metin / başlatma metni önce olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Arguments Yönergesi](xarguments-directive.md)
