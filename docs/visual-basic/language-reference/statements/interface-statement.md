---
title: Interface Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: b606f24cf3baa13746834dfbf7ca6b9215fd3558
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348051"
---
# <a name="interface-statement-visual-basic"></a>Interface Deyimi (Visual Basic)
Bir arabirimin adını bildirir ve arabirimin içerdiği üyelerin tanımlarını tanıtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
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
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [korumalı arkadaş](../../language-reference/modifiers/protected-friend.md)<br/>- [özel korumalı](../../language-reference/modifiers/private-protected.md)<br /><br /> [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Gerekli. Bu arabirimin adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bunun genel bir arabirim olduğunu belirtir.|  
|`typelist`|[Anahtar sözcüğünü](../../../visual-basic/language-reference/statements/of-clause.md) kullanıyorsanız gereklidir. Bu arabirim için tür parametrelerinin listesi. İsteğe bağlı olarak, her tür parametresi `In` ve `Out` genel değiştiriciler kullanılarak değişken olarak bildirilemez. Bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu arabirimin, başka bir arabirim veya arabirimlerin özniteliklerini ve üyelerini devralandığını belirtir. Bkz. [Inherits açıklaması](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|`Inherits` ifadesini kullanıyorsanız gereklidir. Bu arabirimin türettiği arabirimlerin adları.|  
|`modifiers`|İsteğe bağlı. Tanımlanmakta olan arabirim üyesi için uygun değiştiriciler.|  
|`Property`|İsteğe bağlı. Arabirimin üyesi olan bir özelliği tanımlar.|  
|`Function`|İsteğe bağlı. Arabirimin üyesi olan bir `Function` yordamını tanımlar.|  
|`Sub`|İsteğe bağlı. Arabirimin üyesi olan bir `Sub` yordamını tanımlar.|  
|`Event`|İsteğe bağlı. Arabirimin üyesi olan bir olayı tanımlar.|  
|`Interface`|İsteğe bağlı. Bu arabirim içinde iç içe geçmiş bir arabirim tanımlar. İç içe arabirim tanımının bir `End Interface` ifadesiyle sonlandırılması gerekir.|  
|`Class`|İsteğe bağlı. Arabirimin üyesi olan bir sınıfı tanımlar. Üye sınıfı tanımının bir `End Class` ifadesiyle sonlandırılması gerekir.|  
|`Structure`|İsteğe bağlı. Arabirimin üyesi olan bir yapıyı tanımlar. Üye yapısı tanımının bir `End Structure` ifadesiyle sonlandırılması gerekir.|  
|`membername`|Arabirimin bir üyesi olarak tanımlanan her özellik, yordam, olay, arabirim, sınıf veya yapı için gereklidir. Üyenin adı.|  
|`End Interface`|`Interface` tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 *Arabirim* , Özellikler ve yordamlar gibi bir üye kümesini tanımlar, bu sınıfların ve yapıların uygulayabilirler. Arabirim, iç çalışmalarını değil yalnızca üyelerin imzalarını tanımlar.  
  
 Bir sınıf veya yapı, arabirim tarafından tanımlanan her üye için kod sağlayarak arabirimini uygular. Son olarak, uygulama bu sınıf veya yapıdan bir örnek oluşturduğunda, bir nesne var ve bellekte çalışır. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) ve [arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Yalnızca ad alanı veya modül düzeyinde `Interface` kullanabilirsiniz. Bu, bir arabirim için *bildirim bağlamının* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olması gerektiği anlamına gelir ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan olarak, [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişimi için arabirimler. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Arabirimleri iç içe geçirme.** Bir arabirimi diğeri içinde tanımlayabilirsiniz. Dış arabirime *kapsayan arabirim*denir ve iç arabirime *iç içe arabirim*denir.  
  
- **Üye bildirimi.** Bir özelliğin veya yordamın bir arabirimin üyesi olarak bildirimini yaptığınızda, yalnızca bu özelliğin veya yordamın *imzasını* tanımlamanız gerekir. Buna öğe türü (özellik veya yordam), parametreleri ve parametre türleri ve dönüş türü dahildir. Bu nedenle, üye tanımı yalnızca bir kod satırı kullanır ve `End Function` veya `End Property` gibi sonlandırma deyimleri bir arabirimde geçerli değildir.  
  
     Buna karşılık, bir sabit listesi veya yapı ya da iç içe bir sınıf ya da arabirim tanımladığınızda, veri üyelerini eklemek gereklidir.  
  
- **Üye değiştiricileri.** Modül üyelerini tanımlarken erişim değiştiricilerini veya [aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md)hariç [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) ya da herhangi bir yordam değiştiricisini belirtebilirsiniz. [Gölgelerin](../../../visual-basic/language-reference/modifiers/shadows.md)bulunduğu herhangi bir üyeyi bildirebilir ve [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md) veya [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)gibi bir özelliği tanımlarken [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) ' i kullanabilirsiniz.  
  
- **Devralmayı.** Arabirim [Inherits ifadesini](../../../visual-basic/language-reference/statements/inherits-statement.md)kullanıyorsa, bir veya daha fazla temel arabirim belirtebilirsiniz. Her biri aynı ada sahip bir üye tanımlasa bile iki arabirimden devralma yapabilirsiniz. Bunu yaparsanız, uygulama kodunun hangi üyeyi uygulamakta olduğunu belirtmek için ad nitelemesini kullanması gerekir.  
  
     Arabirim, daha kısıtlayıcı erişim düzeyine sahip başka bir arabirimden devralınabilir. Örneğin, bir `Public` arabirimi `Friend` arabiriminden devralınabilir.  
  
     Arabirim, içinde iç içe geçmiş bir arabirimden devralınabilir.  
  
- **Paylaşır.** Bir sınıf bu arabirimi uygulamak için [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) ifadesini kullandığında, arabirim içinde tanımlanan her üyeyi uygulamalıdır. Ayrıca, uygulama kodundaki her imza, bu arabirimde tanımlanan karşılık gelen imzayla tam olarak eşleşmelidir. Ancak, uygulama kodundaki üyenin adı, arabirimde tanımlanan üye adıyla eşleşmek zorunda değildir.  
  
     Bir sınıf bir yordamı uygularken, yordamı `Shared`olarak belirleyemez.  
  
- **Varsayılan özellik.** Arabirim, özellik adı kullanılmadan başvurulabilen en az bir özelliği *varsayılan özelliği*olarak belirtebilir. Böyle bir özelliği [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) değiştiriciyle bildirerek belirtirsiniz.  
  
     Bunun anlamı, bir arabirimin varsayılan bir özelliği yalnızca hiçbiri devralırsa tanımlayabileceğini unutmayın.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Tüm arabirim üyelerinin dolaylı olarak [genel](../../../visual-basic/language-reference/modifiers/public.md) erişimi vardır. Üye tanımlarken herhangi bir erişim değiştiricisi kullanamazsınız. Ancak, arabirimini uygulayan bir sınıf, uygulanan her üye için bir erişim düzeyi bildirebilirler.  
  
     Bir değişkene bir sınıf örneği atarsanız, üyelerinin erişim düzeyi, değişkenin veri türünün temel alınan arabirim veya uygulama sınıfı olmasına bağlı olarak değişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     `varAsInterface`aracılığıyla sınıf üyelerine eriştiğinizde, bunların hepsi ortak erişime sahiptir. Ancak, üyelere `varAsClass`aracılığıyla erişmeniz durumunda `doSomething` `Sub` yordamının özel erişimi vardır.  
  
- **Kapsam.** Arabirim, ad alanı, sınıf, yapı veya modül genelinde kapsamdadır.  
  
     Her arabirim üyesinin kapsamı tüm arabirimdir.  
  
- **Süre.** Bir arabirimin yaşam süresi yoktur ve üyeleri bunu yapmaz. Bir sınıf bir arabirim uygulamışsa ve bu sınıfın bir örneği olarak bir nesne oluşturulduğunda, nesnenin çalıştığı uygulama içinde yaşam süresi vardır. Daha fazla bilgi için bkz. [Class deyimindeki](../../../visual-basic/language-reference/statements/class-statement.md)"Lifetime".  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Property` ifadesiyle ve bir `Function` ifadesiyle uygulanması gereken `thisInterface`adlı bir arabirim tanımlamak için `Interface` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 `Property` ve `Function` deyimlerinin, arabirim içinde `End Property` ve `End Function` biten blokları tanıtmadığını unutmayın. Arabirim yalnızca üyelerinin imzalarını tanımlar. Tam `Property` ve `Function` blokları `thisInterface`uygulayan bir sınıfta görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- ['Ndaki](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Dışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
