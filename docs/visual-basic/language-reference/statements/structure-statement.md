---
title: Structure deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: 9377d889f56049720ab10439582300913f5cbb37
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416447"
---
# <a name="structure-statement"></a>Structure Yapısı
Bir yapının adını bildirir ve değişkenleri, özellikleri, olayları ve yapısını oluşturan yordamların tanımını tanıtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Özel korumalı](../../language-reference/modifiers/private-protected.md) <br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|İsteğe bağlı. Yapının kısmi bir tanımını gösterir. Bkz: [kısmi](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Gerekli. Bu yapının adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Genel amaçlı bir yapı olduğunu belirtir.|  
|`typelist`|İfadesini kullanıyorsanız gereklidir [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Bu yapı için tür parametreleri listesi. Bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|İsteğe bağlı. Bu yapının bir veya daha fazla arabirimin üyelerini uyguladığını belirtir. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Implements` deyimi. Bu yapının uyguladığı arayüzlerin adları.|  
|`datamemberdeclarations`|Gerekli. Sıfır veya daha fazla `Const`, `Dim`, `Enum`, veya `Event` bildiriyor *veri üyeleri* yapısı.|  
|`methodmemberdeclarations`|İsteğe bağlı. Sıfır veya daha fazla bildirimlerini `Function`, `Operator`, `Property`, veya `Sub` gören, *yöntem üyeleri* yapısı.|  
|`End Structure`|Gerekli. Sonlandırır `Structure` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Structure` Deyimi özelleştirebileceğiniz bir bileşik değer türü tanımlar. A *yapısı* Visual Basic'in önceki sürümlerindeki kullanıcı tanımlı tür (UDT) genelleştirilmiş olduğundan. Daha fazla bilgi için [yapıları](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Yapılar sınıflarla aynı özelliklerin çoğunu destekler. Örneğin, yapılar özelliklere ve yordamlara sahip olabilir, arabirimleri uygulayabilir ve parametreli oluşturuculara sahip. Ancak, devralma, bildirimler ve kullanım alanlardaki yapılar ve sınıflar arasında önemli farklılıklar vardır. Ayrıca, sınıflar başvuru, yapılar değer türüdür. Daha fazla bilgi için [yapılar ve sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Kullanabileceğiniz `Structure` yalnızca düzeyinde ad alanında veya modülde. Başka bir deyişle *bildirim içeriğinin* bir yapının kaynak dosyası, ad alanı, sınıf, yapı, modül veya arabirimi olması gerekir ve bir yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Yapılar varsayılan olarak [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **İç içe geçme.** İçindeki başka bir yapı tanımlayabilirsiniz. Dış yapı adlı *içeren yapı*, ve iç yapı adında bir *iç içe geçmiş yapısı*. Ancak içeren yapı ile iç içe geçmiş bir yapının üyelerine erişemezsiniz. Bunun yerine, iç içe geçmiş yapının veri türünde bir değişken bildirmeniz gerekir.  
  
-   **Üye bildirimi.** Bir yapının her üyesini bildirmeniz gerekir. Yapı üyesi olamaz [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) veya `Protected Friend` hiçbir şey bir yapısından devralabileceğinden. Ancak yapının kendisi, olabilir `Protected` veya `Protected Friend`.  
  
     Sıfır veya daha çok paylaşılmayan değişkenler veya paylaşılmayan, özel olmayan olaylar yapısına bildirebilirsiniz. Bazıları paylaşılmayan olsa bile yalnızca sabitler, özellikler ve yordamlar, sahip olamaz.  
  
-   **Başlatma.** Bir yapının bildiriminin bir parçası olarak herhangi bir paylaşılmayan veri üyesinin değerini başlatılamıyor. Böyle bir veri üyesini, yapıdaki parametreli bir kurucu yapısı hakkında başlatmak, veya yapının örneğini oluşturduktan sonra üyeye bir değer atayın.  
  
-   **Devralma.** Bir yapı dışında herhangi bir türden devralamaz <xref:System.ValueType>, öğesinden, tüm devralamaz. Özellikle, bir yapı bir başkasından devralınamaz.  
  
     Kullanamazsınız [devralan deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md) belirtmek için bir yapı tanımında bile <xref:System.ValueType>.  
  
-   **Uygulama.** Yapısı kullanıyorsa [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md), belirttiğiniz her arabirim tarafından tanımlanan her üyeyi uygulamalısınız `interfacenames`.  
  
-   **Varsayılan özellik.** Bir yapı en fazla bir özellik olarak belirtebilirsiniz, *varsayılan özellik*kullanarak [varsayılan](../../../visual-basic/language-reference/modifiers/default.md) değiştiricisi. Daha fazla bilgi için [varsayılan](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bir yapı içerisinde, her bir üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Varsayılan olarak tüm yapı üyeleri [genel](../../../visual-basic/language-reference/modifiers/public.md) erişim. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlama bile daha kısıtlı bir erişim düzeyi yapısı varsa bu otomatik olarak erişim üyelere erişimi kısıtlar.  
  
-   **Kapsam.** Kendi içeren ad alanı, sınıf, yapı veya modül kapsamdadır bir yapıdır.  
  
     Her yapı üyesi kapsamını tamamıdır.  
  
-   **Yaşam süresi.** Bir yapının kendisi bir yaşam süresi yok. Bunun yerine, bu yapının her örneğinin tüm diğer örneklerden bağımsız bir ömrü vardır.  
  
     Bir örneği ömrünü tarafından oluşturulduğunda başlar bir [New işleci](../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi. Tutan değişken ömrü sona erdiğinde sona erer.  
  
     Bir yapı örneğinin ömrünü uzatamazsınız. Statik Yapı işlevselliğine yaklaşık bir tahmin modül tarafından sağlanır. Daha fazla bilgi için [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Yapı üyelerinin ömürleri nasıl ve nerede beyan edildiklerine bağlıdır bağlı olarak var. Daha fazla bilgi için "Ömür" başlığına bakın. [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Nitelik.** Bir yapı dışındaki kod, bir üyenin adını bu yapı adıyla nitelemelidir.  
  
     İç içe bir yapı içinde kod programlama öğesine nitelenmemiş bir başvuru yaparsa, Visual Basic öğe için ilk olarak iç içe yapıda, sonra içeren yapısında ve benzeri en dıştaki içeren öğede arar. Daha fazla bilgi için [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Bellek tüketimi.** Tüm bileşik veri türleri gibi ile güvenli bir şekilde, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini hesaplanamaz. Ayrıca, siparişin bellekteki depolama sırasının bildirim ile aynı olduğunu güvenli bir şekilde varsayamazsınız. Bir yapının depolama düzenini denetlemek için ihtiyacınız varsa, uygulayabilirsiniz <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Structure` deyimi bir çalışan için ilgili veri kümesini tanımlamak için. Kullanımını gösteren `Public`, `Friend`, ve `Private` veri öğelerinin duyarlılığını yansıtmak için üyeleri. Yordam, özellik ve olay üyelerini de gösterir.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Yapılar ve Sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
