---
title: "x:FactoryMethod Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 0d53db49961c2a75e4547f6b57240cefd2cc17c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod Yönergesi
XAML işlemci yedekleme türünü düzelttikten sonra bir nesneyi başlatmak için kullanması gereken bir oluşturucu dışında bir yöntem belirtir.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML öznitelik kullanımı, hiçbir x: Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML öznitelik kullanımı, x: Arguments öğe olarak  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`methodname`|Olarak belirtilen örneği başlatmak için XAML işlemcileri çağıran bir yöntem dize yöntemi adını `object`. Açıklamalar bakın.|  
|`oneOrMoreObjectElements`|Fabrika yöntemi parametrelerini belirtin nesneleri için bir veya daha fazla nesne öğeleri. Sırası önemlidir; bağımsız değişkenler için Üreteç yöntemi iletilmesi gereken sırayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `methodname` bir örnek yöntemidir tam olamaz.  
  
 Statik yöntemler fabrika yöntemi olarak desteklenir. Varsa `methodname` bir statik yöntem `methodname` olarak sağlanan bir *typeName*. *methodName* birleşimi, burada *typeName* statik Üreteç yöntemi tanımlayan sınıf adları. *typeName* öneki nitelenmiş eşlenen xmlns içinde türüne başvuran durumunda olabilir. *typeName* farklı bir type olabilir `typeof(``object``)`.  
  
 Üreteç yöntemi ilgili nesne öğesi yedekler türünde bildirilen bir genel yöntem olması gerekir.  
  
 Üreteç yöntemi ilgili nesnesine atanamaz örneğini döndürmelidir. Fabrika yöntemleri hiçbir zaman null değerini döndürmelidir.  
  
 `x:Arguments`Fabrika yöntemleri, imzaları için en iyi eşleşmeyi prensibi çalıştırır. Eşleşen parametre sayısı önce değerlendirir. Parametre sayısı için birden fazla olası eşleşme varsa, değerlendirilen ve en iyi eşleşme belirlenir sonra parametre türü değil. XAML işlemci davranış hala belirsizlik varsa bu Değerlendirme Aşaması sonra tanımlanmamıştır.  
  
 `x:FactoryMethod` Öğesi kullanımı tipik herkese açık özellik öğesi kullanımı yönerge biçimlendirme içeren nesne öğenin türü başvurmuyor olmadığından değil. Beklenen bu öğe kullanım öznitelik kullanımı daha az yaygındır. `x:Arguments`(öznitelik veya öğe kullanım) ile birlikte kullanılabilir `x:FactoryMethod` öğesi kullanımı, ancak bu özellikle gösterilmez kullanım bölümlerde.  
  
 `x:FactoryMethod`herhangi bir öğe başka bir özellik öğelerinin gelmelidir gibi gelmelidir `x:Arguments` ayrıca öğeleri olarak sağlanan ve herhangi bir içeriği/iç metin/başlatma metin gelmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x: Arguments yönergesi](../../../docs/framework/xaml-services/x-arguments-directive.md)
