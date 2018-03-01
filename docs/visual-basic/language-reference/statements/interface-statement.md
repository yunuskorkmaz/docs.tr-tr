---
title: Interface Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9418dc86ac6947ae951cb8fb757aed6e092a6668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-statement-visual-basic"></a>Interface Deyimi (Visual Basic)
Arabirim adını bildirir ve arabirim oluşur üyeleri tanımlarını sunar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Gerekli. Bu arabirim adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bu genel bir arabirim olduğunu belirtir.|  
|`typelist`|Kullanırsanız, gerekli [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Bu arabirim için tür parametreleri listesi. İsteğe bağlı olarak, her tür parametre değişken kullanarak bildirilebilir `In` ve `Out` genel değiştiricileri. Bkz: [yazın listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu arabirim öznitelikleri ve üyeleri başka bir arabirim veya arabirimler devraldığını gösterir. Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Kullanırsanız, gerekli `Inherits` deyimi. Bu arabirim türetilen arabirimleri adları.|  
|`modifiers`|İsteğe bağlı. Uygun değiştiricileri tanımlanmakta arabirim üyesi için.|  
|`Property`|İsteğe bağlı. Arabirim üyesi olan bir özelliğini tanımlar.|  
|`Function`|İsteğe bağlı. Tanımlayan bir `Function` arabirimi üyesi yordamı.|  
|`Sub`|İsteğe bağlı. Tanımlayan bir `Sub` arabirimi üyesi yordamı.|  
|`Event`|İsteğe bağlı. Arabirim üyesi olan bir olay tanımlar.|  
|`Interface`|İsteğe bağlı. Bu arabirim içinde iç içe bir arabirim tanımlar. İç içe geçmiş arabirim tanımı ile bitmesi bir `End Interface` deyimi.|  
|`Class`|İsteğe bağlı. Arabirim üyesi olan bir sınıfı tanımlar. Üye sınıf tanımı ile bitmesi bir `End Class` deyimi.|  
|`Structure`|İsteğe bağlı. Arabirim üyesi olan bir yapısını tanımlar. Üye yapısı tanımı ile bitmesi bir `End Structure` deyimi.|  
|`membername`|Her özellik, yordam, olay, arabirim, sınıf veya yapı arabirimi bir üyesi olarak tanımlanan için gereklidir. Üyenin adı.|  
|`End Interface`|Sonlandırır `Interface` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir *arabirimi* gibi özellikler ve sınıfları ve yapıları yordamları uygulayabilirsiniz üyelerin kümesini tanımlar. Arabirimi yalnızca, üyeleri ve kendi iç işleyişini imzaları tanımlar.  
  
 Bir sınıf veya yapı arabirimi tarafından tanımlanan her üye için kod sağlayarak arabirimini uygular. Son olarak, uygulama bu sınıf veya yapı örneğini oluşturduğunda, bir nesne var ve bellekte çalıştırır. Daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) ve [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Kullanabileceğiniz `Interface` yalnızca ad alanı veya düzeyinde modülü. Yani *bildirimi bağlam* bir arabirim bir kaynak dosya, ad alanı, sınıf, yapısı, modül veya arabirimi olmalı ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan olarak arabirimleri [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Arabirimleri iç içe geçme.** Başka bir arabirimde tanımlayabilirsiniz. Dış arabirimi adlı *arabirimi içeren*, ve iç arabirimi adlı bir *iç içe geçmiş arabirimi*.  
  
-   **Üye bildirimi.** Yalnızca bir arabirim üye olarak bir özellik veya yordam bildirirken tanımlıyorsanız *imza* bu özellik veya yordam. Bu öğe türü (özellik veya yordam), parametreleri ve parametre türleri ve dönüş türünü içerir. Bu nedenle üye tanımını kodu ve gibi sonlandırma deyimleri yalnızca tek bir çizgi kullanan `End Function` veya `End Property` bir arabirim, geçerli değil.  
  
     Buna karşılık, numaralandırma veya yapısını veya iç içe geçmiş sınıf ya da arabirimi tanımladığınızda, kendi veri üyeleri dahil etmek gerekli.  
  
-   **Üye değiştiricileri.** Erişim değiştiricileri modülü üyeleri tanımlarken kullanamaz ya da belirtebilirsiniz [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) veya dışında herhangi bir yordamı değiştiricisi [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md). İle herhangi bir üyesi bildirebilir [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md), kullanabileceğiniz [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) bir özellik tanımlarken yanı [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md) veya [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Devralma.** Arabirimi kullanıyorsa [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md), bir veya daha fazla temel arabirimleri belirtebilirsiniz. Bunların hepsi aynı ada sahip bir üye tanımlayın olsa bile, iki arabirimlerinden devralabilirsiniz. Bunu yapmak, uygulama kodu ad niteliği uyguladığı hangi üye belirtmek için kullanmanız gerekir.  
  
     Bir arabirim daha kısıtlayıcı erişim düzeyine sahip başka bir arabirim devralınmalıdır olamaz. Örneğin, bir `Public` olamaz arabirimi devralan bir `Friend` arabirimi.  
  
     Bir arabirim içinde iç içe bir arabirimden devralan olamaz.  
  
-   **Uygulaması.** Bir sınıf kullandığında [uygular](../../../visual-basic/language-reference/statements/implements-clause.md) bu arabirimi uygulayan deyimi arabirimde tanımlanan her üye uygulamalıdır. Ayrıca, uygulama kodunda her imza Bu arabiriminde tanımlanan karşılık gelen imza tam olarak eşleşmelidir. Ancak, uygulama kodunda üyenin adını arabiriminde tanımlanan üye adı ile eşleşmesi mevcut değil.  
  
     Bir sınıf bir yordamı uygularken, yordamın olarak belirtemezsiniz `Shared`.  
  
-   **Varsayılan özellik.** Arabirim en çok bir özellik olarak belirtebilirsiniz, *varsayılan özellik*, hangi başvurulabilir özellik adı kullanmadan. Böyle bir özellik ile bildirerek belirttiğiniz [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) değiştiricisi.  
  
     Bu durum yalnızca hiçbiri devralır varsa bir arabirimi varsayılan bir özellik tanımlayabilirsiniz anlamına dikkat edin.  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Tüm arabirimi örtük olarak üyeli [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim. Üye tanımlarken, hiçbir erişim değiştiricisi kullanamazsınız. Ancak, arabirimini uygulayan bir sınıfa uygulanan her üyesi için bir erişim düzeyi bildirebilirsiniz.  
  
     Bir değişken için bir sınıf örneği atarsanız, üyelerine erişim düzeyini değişkeninin veri türü temel alınan arabirimi veya uygulayan sınıfa olan bağlı olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Sınıf üyeleri üzerinden erişirseniz `varAsInterface`, tüm ortak erişimi. Ancak, üyeleri üzerinden erişirseniz `varAsClass`, `Sub` yordam `doSomething` özel erişebilir.  
  
-   **Kapsamı.** Ad alanı, sınıf, yapı veya modülü boyunca kapsamdaki bir arabirimdir.  
  
     Her arabirim üyesini kapsamını tüm arabirimdir.  
  
-   **Yaşam süresi.** Arabirim kendisini bir yaşam süresi yok veya üyeleri yapın. Bir sınıf bir arabirim ve bir nesnenin ne zaman uygular sınıfı, bir yaşam süresi içinde çalıştığı uygulama içinde nesne vardır örneği oluşturulur. Daha fazla bilgi için bkz: "Ömrü" [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Interface` adlı bir arabirim tanımlamak için deyimi `thisInterface`, hangi gerekir uygulanan ile bir `Property` deyimi ve `Function` deyimi.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Unutmayın `Property` ve `Function` deyimleri ile biten blokları tanıtmak değil `End Property` ve `End Function` arabiriminden. Arabirimi yalnızca üyeleri imzalarını tanımlar. Tam `Property` ve `Function` blokları görünür uygulayan bir sınıf `thisInterface`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Genel arabirimlerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
