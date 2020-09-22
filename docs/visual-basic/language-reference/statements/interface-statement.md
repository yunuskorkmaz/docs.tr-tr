---
title: Interface Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 3025adfe8c881a08df3b5f03253510c263c624d1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873222"
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
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Geneldir](../modifiers/public.md)<br />-   [Korunamadı](../modifiers/protected.md)<br />-   [Dost](../modifiers/friend.md)<br />-   [Özelleştirme](../modifiers/private.md)<br />-  [Korumalı arkadaş](../modifiers/protected-friend.md)<br/>- [Özel korumalı](../modifiers/private-protected.md)<br /><br /> [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).|  
|`name`|Gereklidir. Bu arabirimin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bunun genel bir arabirim olduğunu belirtir.|  
|`typelist`|[Anahtar sözcüğünü](of-clause.md) kullanıyorsanız gereklidir. Bu arabirim için tür parametrelerinin listesi. İsteğe bağlı olarak, her tür parametresi `In` ve genel değiştiriciler kullanılarak değişken olarak bildirilemez `Out` . Bkz. [tür listesi](type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu arabirimin, başka bir arabirim veya arabirimlerin özniteliklerini ve üyelerini devralandığını belirtir. Bkz. [Inherits açıklaması](inherits-statement.md).|  
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Inherits` . Bu arabirimin türettiği arabirimlerin adları.|  
|`modifiers`|İsteğe bağlı. Tanımlanmakta olan arabirim üyesi için uygun değiştiriciler.|  
|`Property`|İsteğe bağlı. Arabirimin üyesi olan bir özelliği tanımlar.|  
|`Function`|İsteğe bağlı. `Function`Arabirimin üyesi olan bir yordamı tanımlar.|  
|`Sub`|İsteğe bağlı. `Sub`Arabirimin üyesi olan bir yordamı tanımlar.|  
|`Event`|İsteğe bağlı. Arabirimin üyesi olan bir olayı tanımlar.|  
|`Interface`|İsteğe bağlı. Bu arabirim içinde iç içe geçmiş bir arabirim tanımlar. İç içe arabirim tanımının bir ifadesiyle sonlandırılması gerekir `End Interface` .|  
|`Class`|İsteğe bağlı. Arabirimin üyesi olan bir sınıfı tanımlar. Üye sınıfı tanımının bir ifadesiyle sonlandırılması gerekir `End Class` .|  
|`Structure`|İsteğe bağlı. Arabirimin üyesi olan bir yapıyı tanımlar. Üye yapısı tanımının bir ifadesiyle sonlandırılması gerekir `End Structure` .|  
|`membername`|Arabirimin bir üyesi olarak tanımlanan her özellik, yordam, olay, arabirim, sınıf veya yapı için gereklidir. Üyenin adı.|  
|`End Interface`|Tanımı sonlandırır `Interface` .|  
  
## <a name="remarks"></a>Açıklamalar  

 *Arabirim* , Özellikler ve yordamlar gibi bir üye kümesini tanımlar, bu sınıfların ve yapıların uygulayabilirler. Arabirim, iç çalışmalarını değil yalnızca üyelerin imzalarını tanımlar.  
  
 Bir sınıf veya yapı, arabirim tarafından tanımlanan her üye için kod sağlayarak arabirimini uygular. Son olarak, uygulama bu sınıf veya yapıdan bir örnek oluşturduğunda, bir nesne var ve bellekte çalışır. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md) ve [arabirimler](../../programming-guide/language-features/interfaces/index.md).  
  
 `Interface`Yalnızca ad alanı veya modül düzeyinde kullanabilirsiniz. Bu, bir arabirim için *bildirim bağlamının* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olması gerektiği anlamına gelir ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan olarak, [arkadaş](../modifiers/friend.md) erişimi için arabirimler. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Arabirimleri iç içe geçirme.** Bir arabirimi diğeri içinde tanımlayabilirsiniz. Dış arabirime *kapsayan arabirim*denir ve iç arabirime *iç içe arabirim*denir.  
  
- **Üye bildirimi.** Bir özelliğin veya yordamın bir arabirimin üyesi olarak bildirimini yaptığınızda, yalnızca bu özelliğin veya yordamın *imzasını* tanımlamanız gerekir. Buna öğe türü (özellik veya yordam), parametreleri ve parametre türleri ve dönüş türü dahildir. Bu nedenle, üye tanımı yalnızca bir kod satırı kullanır ve ya da gibi sonlandırma deyimleri `End Function` `End Property` arabirim içinde geçerli değildir.  
  
     Buna karşılık, bir sabit listesi veya yapı ya da iç içe bir sınıf ya da arabirim tanımladığınızda, veri üyelerini eklemek gereklidir.  
  
- **Üye değiştiricileri.** Modül üyelerini tanımlarken erişim değiştiricilerini veya [aşırı yüklemeler](../modifiers/overloads.md)hariç [paylaşılan](../modifiers/shared.md) ya da herhangi bir yordam değiştiricisini belirtebilirsiniz. [Gölgelerin](../modifiers/shadows.md)bulunduğu herhangi bir üyeyi bildirebilir ve [salt okunur](../modifiers/readonly.md) veya [WriteOnly](../modifiers/writeonly.md)gibi bir özelliği tanımlarken [varsayılan](../modifiers/default.md) ' i kullanabilirsiniz.  
  
- **Devralmayı.** Arabirim [Inherits ifadesini](inherits-statement.md)kullanıyorsa, bir veya daha fazla temel arabirim belirtebilirsiniz. Her biri aynı ada sahip bir üye tanımlasa bile iki arabirimden devralma yapabilirsiniz. Bunu yaparsanız, uygulama kodunun hangi üyeyi uygulamakta olduğunu belirtmek için ad nitelemesini kullanması gerekir.  
  
     Arabirim, daha kısıtlayıcı erişim düzeyine sahip başka bir arabirimden devralınabilir. Örneğin, bir `Public` arabirim `Friend` arabiriminden devralınabilir.  
  
     Arabirim, içinde iç içe geçmiş bir arabirimden devralınabilir.  
  
- **Paylaşır.** Bir sınıf bu arabirimi uygulamak için [Implements](implements-clause.md) ifadesini kullandığında, arabirim içinde tanımlanan her üyeyi uygulamalıdır. Ayrıca, uygulama kodundaki her imza, bu arabirimde tanımlanan karşılık gelen imzayla tam olarak eşleşmelidir. Ancak, uygulama kodundaki üyenin adı, arabirimde tanımlanan üye adıyla eşleşmek zorunda değildir.  
  
     Bir sınıf bir yordamı uygularken, yordamı olarak belirleyemez `Shared` .  
  
- **Varsayılan özellik.** Arabirim, özellik adı kullanılmadan başvurulabilen en az bir özelliği *varsayılan özelliği*olarak belirtebilir. Böyle bir özelliği [varsayılan](../modifiers/default.md) değiştiriciyle bildirerek belirtirsiniz.  
  
     Bunun anlamı, bir arabirimin varsayılan bir özelliği yalnızca hiçbiri devralırsa tanımlayabileceğini unutmayın.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Tüm arabirim üyelerinin dolaylı olarak [genel](../modifiers/public.md) erişimi vardır. Üye tanımlarken herhangi bir erişim değiştiricisi kullanamazsınız. Ancak, arabirimini uygulayan bir sınıf, uygulanan her üye için bir erişim düzeyi bildirebilirler.  
  
     Bir değişkene bir sınıf örneği atarsanız, üyelerinin erişim düzeyi, değişkenin veri türünün temel alınan arabirim veya uygulama sınıfı olmasına bağlı olarak değişebilir. Aşağıdaki örnek bunu göstermektedir.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Aracılığıyla sınıf üyelerine eriştiğinizde `varAsInterface` , bunların hepsi ortak erişime sahiptir. Ancak, üyelere aracılığıyla eriştiğinizde `varAsClass` , `Sub` yordamda `doSomething` özel erişimi vardır.  
  
- **Kapsam.** Arabirim, ad alanı, sınıf, yapı veya modül genelinde kapsamdadır.  
  
     Her arabirim üyesinin kapsamı tüm arabirimdir.  
  
- **Süre.** Bir arabirimin yaşam süresi yoktur ve üyeleri bunu yapmaz. Bir sınıf bir arabirim uygulamışsa ve bu sınıfın bir örneği olarak bir nesne oluşturulduğunda, nesnenin çalıştığı uygulama içinde yaşam süresi vardır. Daha fazla bilgi için bkz. [Class deyimindeki](class-statement.md)"Lifetime".  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Interface` `thisInterface` bir `Property` ifadesiyle ve ifadesiyle uygulanması gereken adlı bir arabirimi tanımlamak için ifadesini kullanır `Function` .  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 `Property`Ve `Function` deyimlerinin, `End Property` arabirim içinde ve arasında biten blokları tanıtmadığını unutmayın `End Function` . Arabirim yalnızca üyelerinin imzalarını tanımlar. Tam `Property` ve `Function` blokları, uygulayan bir sınıfta görüntülenir `thisInterface` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)
- [Class Deyimi](class-statement.md)
- [Module Deyimi](module-statement.md)
- [Structure Yapısı](structure-statement.md)
- [Property Deyimi](property-statement.md)
- [Function Deyimi](function-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Genel Arabirimlerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [İçinde](../modifiers/in-generic-modifier.md)
- [Dışı](../modifiers/out-generic-modifier.md)
