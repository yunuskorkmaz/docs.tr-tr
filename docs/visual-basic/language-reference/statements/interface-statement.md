---
title: Interface Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: db39759a804905450e7f8913f45e8ddab39d8416
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823538"
---
# <a name="interface-statement-visual-basic"></a>Interface Deyimi (Visual Basic)
Bir arabirimin adını bildirir ve arabirimi oluşturan üyelerin tanımlarını sunmaktadır.  
  
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
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Özel korumalı](../../language-reference/modifiers/private-protected.md)<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Gerekli. Bu arabirimin adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bu genel bir arabirim olduğunu belirtir.|  
|`typelist`|İfadesini kullanıyorsanız gereklidir [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Bu arabirim için tür parametreleri listesi. İsteğe bağlı olarak, her tür parametresi değişken kullanarak bildirilebilir `In` ve `Out` genel değiştiriciler. Bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu arabirim öznitelikleri ve üyeleri başka bir arabirim veya arabirimleri devraldığını gösterir. Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Inherits` deyimi. Bu arabirim türetildiği arayüzlerin adları.|  
|`modifiers`|İsteğe bağlı. Tanımlanan arabirim üyesi için uygun değiştiriciler.|  
|`Property`|İsteğe bağlı. Arabirimin bir üyesi olan bir özelliğini tanımlar.|  
|`Function`|İsteğe bağlı. Tanımlayan bir `Function` arabirimin üyesi yordamı.|  
|`Sub`|İsteğe bağlı. Tanımlayan bir `Sub` arabirimin üyesi yordamı.|  
|`Event`|İsteğe bağlı. Arabirimin bir üyesi olan bir olayı tanımlar.|  
|`Interface`|İsteğe bağlı. Bu arabirim içinde iç içe bir arabirim tanımlar. İç içe geçmiş arabirim tanımı ile bitmesi bir `End Interface` deyimi.|  
|`Class`|İsteğe bağlı. Arabirimin bir üyesi olan bir sınıfı tanımlar. Üye sınıfı tanımı ile bitmesi bir `End Class` deyimi.|  
|`Structure`|İsteğe bağlı. Arabirimin bir üyesi olan bir yapı tanımlar. Üye yapı tanımı ile bitmesi bir `End Structure` deyimi.|  
|`membername`|Her özellik, yordam, olay, arabirim, sınıf veya yapının arabirimin bir üyesi tanımlanan için gereklidir. Üyenin adı.|  
|`End Interface`|Sonlandırır `Interface` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir *arabirimi* gibi özelliklere ve yordamlara sınıfları ve yapıları uygulayabilir, üyelerin kümesini tanımlar. Arabirimi yalnızca üyeleri ve kendi iç işleyişini imzalarını tanımlar.  
  
 Bir sınıf veya yapı, arabirim tarafından tanımlanan her üye için kod sağlanarak arabirimi uygular. Son olarak, bu sınıf ya da yapı uygulama örneği oluşturur, bir nesne var ve bellekte çalıştırır. Daha fazla bilgi için [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) ve [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Kullanabileceğiniz `Interface` yalnızca düzeyinde ad alanında veya modülde. Başka bir deyişle *bildirim içeriğinin* bir arabirim bir kaynak dosyası, ad alanı, sınıf, yapı, modül veya arabirimi olması gerekir ve bir yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan olarak arabirimleri [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Arabirim iç içe geçirme.** İçindeki başka bir arabirim tanımlayabilirsiniz. Dış arabirimi adlı *arabirimi içeren*, ve iç arabirimi olarak adlandırılan bir *iç içe geçmiş arabirimi*.  
  
-   **Üye bildirimi.** Yalnızca bir arabirimin bir üyesi bir özellik veya yordamı bildirdiğinizde tanımlıyorsanız *imza* bu özellik veya yordamı. Bu öğe türü (özellik ya da yordamın), parametreleri ve parametre türleri ve dönüş türü içerir. Bu nedenle, kod ve gibi Sonlandırıcı deyimler yalnızca bir satırı üye tanımı kullanan `End Function` veya `End Property` bir arabirimde geçerli değildir.  
  
     Buna karşılık, bir numaralandırma veya yapısı, veya bir iç içe geçmiş sınıf veya arabirim tanımladığınızda, veri üyeleri dahil etmek gereklidir.  
  
-   **Üye değiştiriciler.** Tüm erişim değiştiricileri modülü üyeleri tanımlarken kullanamaz ya da belirtebilirsiniz [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) veya dışında herhangi bir yordam değiştiricisi [aşırı](../../../visual-basic/language-reference/modifiers/overloads.md). Herhangi bir üyesi ile bildirebilirsiniz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md), kullanabileceğiniz [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) bir özellik tanımlarken yanı [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md) veya [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Devralma.** Arabirim kullanıyorsa [devralan deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md), bir veya daha fazla temel arabirimde belirtebilirsiniz. Bunların hepsi aynı ada sahip bir üye tanımlarsanız bile iki ara birimden devralınabilir. Bunu yaparsanız uyguladığı üye belirtmek için uygulanan kodun ad niteliği kullanmanız gerekir.  
  
     Bir arabirim daha kısıtlayıcı bir erişim düzeyi olan başka bir arabirimden devralamaz. Örneğin, bir `Public` arabirimi öğesinden özellik devralamaz bir `Friend` arabirimi.  
  
     Bir arabirim, kendi içinde iç içe bir arabirimden devralamaz.  
  
-   **Uygulama.** Bir sınıf kullandığında [uygular](../../../visual-basic/language-reference/statements/implements-clause.md) bu arabirimi uygulayan deyimini arabirimi içinde tanımlanan her üyeyi uygulamalısınız. Ayrıca, her imza uygulama kodunda bu arabirim içinde tanımlanmış karşılık gelen imzası tam olarak eşleşmelidir. Ancak, uygulama kodundaki üyesinin adı arabirim içinde tanımlanmış üye adıyla eşleşmesi yok.  
  
     Bir sınıf bir yordam uygularken yordamı belirtemezsiniz `Shared`.  
  
-   **Varsayılan özellik.** Bir arabirim en fazla bir özellik olarak belirtebilirsiniz, *varsayılan özellik*, hangi başvurulabilir özellik adını kullanarak olmadan. Böyle bir özellik ile bildirerek belirttiğiniz [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) değiştiricisi.  
  
     Bu durum yalnızca hiçbiri devralırsa bir arabirimi varsayılan bir özelliği tanımlayabilirsiniz anlamına olduğuna dikkat edin.  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Örtük olarak tüm arabirim üyelerinin olması [genel](../../../visual-basic/language-reference/modifiers/public.md) erişim. Tüm erişim değiştiricisi üye tanımlarken kullanamazsınız. Ancak, arabirimini uygulayan bir sınıfa uygulanan her üyesi için bir erişim düzeyi bildirebilirsiniz.  
  
     Bir sınıf örneği bir değişkene atarsanız, üyelerine erişim düzeyini değişkeninin veri türü temel alınan arabirimi veya uygulama sınıfı olmasına göre değişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Sınıf üyeleri aracılığıyla erişiyorsanız `varAsInterface`, ortak erişime sahip oldukları tüm. Ancak, üyeleri aracılığıyla erişiyorsanız `varAsClass`, `Sub` yordamı `doSomething` özel erişimi vardır.  
  
-   **Kapsam.** Ad alanı, sınıf, yapı veya modül kapsamdadır bir arabirimdir.  
  
     Her arabirim üyesini kapsamını tüm arabirimidir.  
  
-   **Yaşam süresi.** Bir arabirim kendisi bir yaşam süresi yok ya da üyelerini yapın. Bir arabirim ve nesnenin ne zaman arabirimini uygulayan bir sınıf sınıfı nesne bir yaşam süresi içinde çalıştığı uygulama içinde olan bir örneği olarak oluşturulur. Daha fazla bilgi için "Ömür" başlığına bakın. [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Interface` adlı bir arabirim tanımlamak için deyimi `thisInterface`, hangi uygulanmalı ile bir `Property` deyimi ve `Function` deyimi.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Unutmayın `Property` ve `Function` deyimleri ile biten bloklarını tanıtır değil `End Property` ve `End Function` arabiriminden. Arabirim üyeleri yalnızca imzalarını tanımlar. Tam `Property` ve `Function` bloklarını uygulayan bir sınıf içinde görünen `thisInterface`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Çıkış](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
