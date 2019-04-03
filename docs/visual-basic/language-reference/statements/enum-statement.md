---
title: Enum Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: fa97a374d4570e014222bf44844271b3394453da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830077"
---
# <a name="enum-statement-visual-basic"></a>Enum Deyimi (Visual Basic)
Bir sabit listesi bildirir ve üyelerinin değerlerini tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `attributelist`  
  
     İsteğe bağlı. Bu sabit listesi için geçerli olan özniteliklerin listesi. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").  
  
     <xref:System.FlagsAttribute> Özniteliği örneği numaralandırma değerini birden fazla numaralandırma üyelerini içerebilir ve her üyesi bir bit alanı numaralandırma değeri temsil ettiğini gösterir.  
  
-   `accessmodifier`  
  
     İsteğe bağlı. Bu sabit listesi kod erişip belirtir. Aşağıdakilerden biri olabilir:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     İsteğe bağlı. Bu numaralandırma redeclares ve bir programlama aynı adlı bir öğeyi veya taban sınıfında aşırı yüklenmiş bir öğe kümesini gizler belirtir. Belirtebileceğiniz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) yalnızca numaralandırma, tüm üyeleri üzerinde değil.  
  
-   `enumerationname`  
  
     Gerekli. Sabit listesinin adı. Geçerli adlar hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     İsteğe bağlı. Sabit listesi ve tüm üyeleri veri türü.  
  
-   `memberlist`  
  
     Gerekli. Bu deyiminde bildirilen üye sabit listesi. Birden çok üye bağımsız kaynak kod satırlarında görünür.  
  
     Her `member` aşağıdaki söz dizimini ve bölümleri vardır: `[<attribute list>] member name [ = initializer ]`  
  
    |Bölümü|Açıklama|  
    |---|---|  
    |`membername`|Gerekli. Bu üyenin adı.|  
    |`initializer`|İsteğe bağlı. Derleme zamanında değerlendirilir ve bu üye için atanan ifade.|  
  
-   `End``Enum`  
  
     Sonlandırır `Enum` blok.  
  
## <a name="remarks"></a>Açıklamalar  
 Mantıksal olarak birbiriyle ilişkili değişmeyen değerlerini bir dizi varsa, bunları bir numaralandırmada birlikte tanımlayabilirsiniz. Bu sabit listesi ve bunların değerlerini kolay üyelerini için anlamlı adlar sağlar. Daha sonra kodunuzda pek çok yerde numaralandırma üyelerini kullanabilirsiniz.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
-   Sırasını değiştirme ya da sayı yanlış yazmanız kaynaklanan hataları azaltır.  
  
-   Değerleri gelecekte değiştirilmesini daha kolay hale getirir.  
  
-   Hataları görülecektir olasılığını olduğu anlamına gelir, daha kolay kodu sağlar.  
  
-   İleriye dönük uyumluluk sağlar. Numaralandırmalar kullanırsanız, kodunuzu gelecekte birinin üyesi adlara karşılık gelen değerleri değişirse başarısız etkilenme olasılığı da düşer.  
  
 Bir numaralandırma bir ad, temel alınan bir veri türü ve bir üye kümesi vardır. Her üye bir sabiti temsil eder.  
  
 Sınıfı, yapı, modül veya dışında herhangi bir yordam arabirimi düzeyinde bildirilen bir sabit listesidir bir *üye numaralandırması*. Sınıfı, yapısı, modül veya onu bildiren arabirimin bir üyesidir.  
  
 Üye numaralandırmalar öğesinden herhangi bir yerde kendi sınıf, yapı, modül veya arabirimi içinde erişilebilir. Kod bir sınıf dışında yapısını veya modülünü Bu sınıf, yapı veya modül adını bir üye sabit listesinin adıyla nitelemeniz gerekir. Tam olarak nitelenmiş adlar ekleyerek kullanmaya gerek kaçınabilirsiniz bir [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bildirimi kaynak dosyası.  
  
 Ad alanı düzeyinde sınıf, yapı, modül veya arabirimi, dışında bildirilen bir numaralandırma göründüğü ad alanının bir üyesidir.  
  
 *Bildirim içeriğinin* numaralandırması bir kaynak dosyası, ad alanı, sınıf, yapı, modül veya arabirimi olması gerekir ve bir yordam olamaz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Öznitelikleri numaralandırması bir bütün olarak, ancak üyelerini tek tek uygulayabilirsiniz. Bir özniteliği derleme meta bilgileri katkıda bulunur.  
  
## <a name="data-type"></a>Veri Türü  
 `Enum` Deyimi, veri türü bir numaralandırmanın bildirebilirsiniz. Her üye, sabit listesinin veri türünü alır. Belirtebileceğiniz `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort`.  
  
 Siz belirtmezseniz `datatype` sabit listesi için her üye veri türünü alır. kendi `initializer`. Her ikisini de belirtirseniz `datatype` ve `initializer`, veri türü `initializer` dönüştürülebilmelidir `datatype`. Kullanılmazsa `datatype` ya da `initializer` varsa, veri türü için varsayılan değerleri `Integer`.  
  
## <a name="initializing-members"></a>Üyeleri başlatma  
 `Enum` Deyimi Seçili üyelerin içeriğini başlatmak `memberlist`. Kullandığınız `initializer` üyesine atanmış bir ifade sağlamanız için.  
  
 Siz belirtmezseniz `initializer` bir üye için Visual Basic ya da sıfırdan başlatır (ilk ise `member` içinde `memberlist`), ya da tek hemen önceki ait olandan daha büyük bir değere `member`.  
  
 Her sağlanan ifade `initializer` değişmez değerleri, önceden tanımlanmış diğer sabitleri ve zaten, önceki bu sabit listesi üyesi de dahil olmak üzere tanımlanan numaralandırma üyeleri herhangi bir birleşimi olabilir. Bu öğeleri birleştirin, aritmetik ve mantıksal işleçlerini kullanabilirsiniz.  
  
 Değişkenler veya işlevlerinde kullanılamaz `initializer`. Bununla birlikte, dönüşüm anahtar sözcükleri gibi kullanabileceğiniz `CByte` ve `CShort`. Ayrıca `AscW` bir sabit ile çağırırsanız `String` veya `Char` bağımsız değişkeni, derleme zamanında değerlendirilebilen olduğundan.  
  
 Numaralandırmalar, kayan nokta değerlerine sahip olamaz. Üye bir kayan noktalı değere atanırsa ve `Option Strict` , bir derleyici hatası oluşursa ayarlanır. Varsa `Option Strict` kapalıysa, değer otomatik olarak dönüştürülür `Enum` türü.  
  
 Temel alınan veri türü için izin verilen aralık bir üyenin değerini aşarsa veya herhangi bir üyesi temel alınan veri türü tarafından izin verilen en yüksek değere başlatmak, derleyici bir hata bildirir.  
  
## <a name="modifiers"></a>Değiştiriciler  
 Sınıfı, yapı, modül ve arabirim üyesi numaralandırmalar varsayılan genel erişim için. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz. Namespace üye numaralandırmalar varsayılan'öğesine friend erişimi için. Genel, ancak özel veya korumalı, erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Tüm numaralandırma üyelerini genel erişimi vardır ve bunlar üzerinde herhangi bir erişim değiştiricileri kullanamazsınız. Numaralandırma, daha kısıtlı bir erişim düzeyi varsa, ancak belirtilen numaralandırma erişim düzeyi önceliklidir.  
  
 Varsayılan olarak, tüm numaralandırmalar türleridir ve onların alanları sabittir. Bu nedenle `Shared`, `Static`, ve `ReadOnly` numaralandırma veya üyelerinin bildirirken, anahtar sözcükler kullanılamaz.  
  
## <a name="assigning-multiple-values"></a>Birden çok değer atama  
 Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder. Ekleyerek <xref:System.FlagsAttribute> özniteliğini `Enum` bildirimi, bunun yerine atayabilirsiniz birden çok değer numaralandırma örneği. <xref:System.FlagsAttribute> Özniteliği sabit listesi flags diğer bir deyişle, bir dizi bir bit alanı olarak değerlendirilmesi belirtir. Bunlar adlandırılır *bit düzeyinde* numaralandırma.  
  
 Kullanarak bir numaralandırma bildirdiğinizde <xref:System.FlagsAttribute> özniteliği öneririz, 2, 1, 2, 4, 8, 16 ve benzeri tabanların değerlerini kullanın. Ayrıca, "None" değeri 0 olan bir üyenin adını olmasını öneririz. Ek yönergeler için bkz: <xref:System.FlagsAttribute> ve <xref:System.Enum>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `Enum` deyimi. Üye olarak adlandırılır Not `EggSizeEnum.Medium`, olarak değil `Medium`.  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte yöntemi dışında `Egg` sınıfı. Bu nedenle, `EggSizeEnum` olarak tam olarak `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Enum` ilgili bir kümesini tanımlamak için deyimi adlı sabit değerler. Bu durumda, bir veritabanı için veri girişi formları tasarlama tercih edebileceğiniz renkleri değerlerdir.  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, pozitif ve negatif sayıları içeren değerleri gösterir.  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir `As` yan tümcesini belirtmek için kullanılır `datatype` bir numaralandırma.  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bit düzeyinde bir numaralandırma kullanma işlemini gösterir. Bit düzeyinde bir sabit listesi örneğini birden çok değer atanabilir. `Enum` Bildirimi içeren <xref:System.FlagsAttribute> özniteliği sabit listesi flags bir dizi ele alınıp alınamayacağını belirtir.  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sabit listesi yinelenir. Kullandığı <xref:System.Enum.GetNames%2A> sabit listesinden alınmış üye adlarının dizisini almak için yöntemi ve <xref:System.Enum.GetValues%2A> üye değerler dizisini almak için.  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Sabitler ve Sabit Listeleri](../../../visual-basic/language-reference/constants-and-enumerations.md)
