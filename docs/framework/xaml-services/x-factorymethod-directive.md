---
title: x:FactoryMethod Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053783"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod Yönergesi
Bir XAML işlemcisinin, kendi destek türünü çözümledikten sonra bir nesneyi başlatmak için kullanması gereken bir Oluşturucu dışında bir yöntemi belirtir.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML öznitelik kullanımı, x:Arguments yok  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML öznitelik kullanımı, x:Arguments öğe (ler) olarak  
  
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
|`methodname`|XAML işlemcilerin, olarak `object`belirtilen örneği başlatmak için çağrı yapan yöntemin dize yöntemi adı. Bkz. açıklamalar.|  
|`oneOrMoreObjectElements`|Fabrika Yöntemi parametrelerini belirten nesneler için bir veya daha fazla nesne öğesi. Sıra önemlidir; bağımsız değişkenlerin fabrika yöntemine geçirilmesi gereken sırayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `methodname` Bir örnek yöntemi ise, nitelenemez.  
  
 Fabrika yöntemleri olarak statik yöntemler desteklenir. Statik bir yöntem ise, `methodname` typeName olarak sağlanır. `methodname`  *methodName* birleşimi, *TypeName* , statik fabrika yöntemini tanımlayan sınıfın adını belirler. *TypeName* , eşlenmiş bir xmlns içindeki bir türe başvurulduğunda önek nitelenebilir. *TypeName* , öğesinden `typeof(object)`farklı bir tür olabilir.  
  
 Factory yöntemi, ilgili nesne öğesini yedekleyen türün tanımlanmış bir ortak yöntemi olmalıdır.  
  
 Factory yöntemi, ilgili nesneye atanabilen bir örnek döndürmelidir. Fabrika yöntemleri asla null döndürmemelidir.  
  
 `x:Arguments`Fabrika yöntemlerinin imzaları için en iyi eşleşme ilkesi üzerinde çalışır. Eşleşen parametre sayısını önce değerlendirir. Bir parametre sayısı için birden fazla olası eşleşme varsa, parametre türü değerlendirilir ve en iyi eşleşme belirlenir. Bu değerlendirme aşamasından sonra hala belirsizlik varsa XAML işlemci davranışı tanımsızdır.  
  
 Yönerge biçimlendirmesi kapsayan nesne öğesinin türüne başvurmadığından, öğekullanımıtipikanlamdaÖzelliköğesikullanımıdeğildir.`x:FactoryMethod` Öğe kullanımının öznitelik kullanımından daha az yaygın olması beklenmektedir. `x:Arguments`(öznitelik veya öğe kullanımı) öğe kullanımı ile `x:FactoryMethod` birlikte kullanılabilir, ancak bu özellikle kullanım bölümlerinde gösterilmez.  
  
 `x:FactoryMethod`bir öğe, diğer tüm özellik öğelerinden önce gelmeli, `x:Arguments` öğeler olarak sağlanmasının ve tüm içerik/iç metin/başlatma metininin önüne gelmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [x:Arguments Yönergesi](x-arguments-directive.md)
