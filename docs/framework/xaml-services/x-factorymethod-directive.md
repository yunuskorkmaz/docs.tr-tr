---
title: x:FactoryMethod Yönergesi
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 436caa9b93467dcf2a0763bcc0962a2beb722315
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560201"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod Yönergesi
XAML işlemci yedekleme türünü çözdükten sonra nesneyi başlatmak için kullanması gereken bir oluşturucu dışında bir yöntem belirtir.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML öznitelik kullanımı, x: Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML öznitelik kullanımı, x: Arguments öğeyi/öğeleri olarak  
  
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
|`methodname`|Dize olarak belirtilen örneği başlatmak için XAML işlemci çağıran bir yöntem yöntemi adını `object`. Açıklamalara bakın.|  
|`oneOrMoreObjectElements`|Fabrika yöntem parametreleri belirtin nesneleri için bir veya daha fazla nesne öğeleri. Sırası önemlidir; Bu bağımsız değişkenler için Üreteç yöntemi iletilmesi gereken sırayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `methodname` bir örnek yöntemi olduğundan koşullu olamaz.  
  
 Statik yöntemler olarak Fabrika yöntemleri desteklenir. Varsa `methodname` statik bir yöntem `methodname` olarak sağlanan bir *typeName*. *methodName* birleşimi, burada *typeName* statik fabrika yöntemi tanımlayan sınıf adları. *typeName* ön ek nitelikli eşlenen xmlns içerisindeki bir türe başvuran durumunda olabilir. *typeName* farklı bir tür olabilir `typeof(object)`.  
  
 İlgili nesne öğesi yedekler türünde bildirilen genel bir yöntem Üreteç yöntemi olmalıdır.  
  
 Üreteç yöntemi ilgili nesneye atanamaz örneği döndürmelidir. Fabrika yöntemleri hiçbir zaman null değeri döndürmelidir.  
  
 `x:Arguments` Fabrika yöntemleri imzalarını için en iyi eşleşme İlkesi çalışır. Eşleşen ilk parametre sayısı değerlendirir. Parametre sayısı için birden çok olası eşleşme varsa, değerlendirilen ve en iyi eşleşme belirlenir sonra parametre türüdür. Varsa hala belirsizlik değerlendirme sonra bu aşamayı, XAML işlemci davranış tanımsızdır.  
  
 `x:FactoryMethod` Öğesi kullanımı değil özellik öğesi kullanımı tipik anlamında yönerge biçimlendirme içeren nesne öğe türünün başvurmadığından. Bu beklenen bu öğesi kullanımı öznitelik kullanımı daha az yaygındır. `x:Arguments` (özniteliği veya öğenin kullanım) ile birlikte kullanılabilir `x:FactoryMethod` öğesi kullanımı, ancak bu özellikle gösterilmez kullanım bölümlerde.  
  
 `x:FactoryMethod` herhangi bir öğeyi diğer bir özelliği öğelerden önce gelmelidir gibi gelmelidir `x:Arguments` ayrıca öğeleri olarak sağlanan ve herhangi bir içeriği/iç metin/başlatma metin gelmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:Arguments Yönergesi](../../../docs/framework/xaml-services/x-arguments-directive.md)
