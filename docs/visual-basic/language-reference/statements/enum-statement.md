---
title: Enum Deyimi
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
ms.openlocfilehash: 48220fd1e88cf38e67db5dd3a2ad90638eb6b6df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343709"
---
# <a name="enum-statement-visual-basic"></a>Enum Deyimi (Visual Basic)

Bir sabit listesi bildirir ve üyelerinin değerlerini tanımlar.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>Bölümler

- `attributelist`

  İsteğe bağlı. Bu sabit listesi için uygulanan özniteliklerin listesi. [Öznitelik listesini](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç içine almalısınız ("`<`" ve "`>`").

  <xref:System.FlagsAttribute> özniteliği, sabit listesinin bir örneğinin değerinin birden çok numaralandırma üyesi içerebileceğini ve her üyenin numaralandırma değerindeki bir bit alanını temsil ettiğini gösterir.

- `accessmodifier`

  İsteğe bağlı. Bu numaralandırmaya erişebilecek kodu belirtir. Aşağıdakilerden biri olabilir:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  İsteğe bağlı. Bu sabit listesinin, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesini yeniden bildirdiğini ve gizlediğini belirtir. Her üye üzerinde değil, yalnızca Numaralandırmadaki [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) belirtebilirsiniz.

- `enumerationname`

  Gerekli. Sabit listesinin adı. Geçerli adlar hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  İsteğe bağlı. Numaralandırmanın ve tüm üyelerinin veri türü.

- `memberlist`

  Gerekli. Bu bildirimde bildirildiği üye sabitlerinin listesi. Tek tek kaynak kodu satırlarında birden çok üye görüntülenir.

  Her `member` aşağıdaki söz dizimi ve bölümlere sahiptir: `[<attribute list>] member name [ = initializer ]`

  |Bölümüyle|Açıklama|
  |---|---|
  |`membername`|Gerekli. Bu üyenin adı.|
  |`initializer`|İsteğe bağlı. Derleme zamanında değerlendirilen ve bu üyeye atanan ifade.|

- `End``Enum`

  `Enum` bloğunu sonlandırır.

## <a name="remarks"></a>Açıklamalar

Mantıksal olarak birbirleriyle ilgili değişmeyen bir değerler kümesi varsa, bunları bir numaralandırmada birlikte tanımlayabilirsiniz. Bu, sabit listesi ve üyeleri için değerlerinden daha kolay anımsanacak anlamlı adlar sağlar. Daha sonra, sabit listesi üyelerini kodunuzda birçok yerde kullanabilirsiniz.

Numaralandırmalar kullanmanın avantajları şunlardır:

- Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.

- Gelecekte değerlerin değiştirilmesini kolaylaştırır.

- Kodun daha kolay okunmasını sağlar, bu da hataların tanıtılmasından daha az olabilir.

- İleriye dönük uyumluluğu sağlar. Numaralandırmalar kullanıyorsanız, gelecekte birisinin üye adlarına karşılık gelen değerleri değiştirmesinin ardından kodunuzun başarısız olma olasılığı düşüktür.

Bir numaralandırma bir ada, temel alınan veri türüne ve bir üye kümesine sahiptir. Her üye bir sabiti temsil eder.

Sınıf, yapı, modül veya arabirim düzeyinde tanımlanan ve herhangi bir yordamın dışında bir numaralandırma, bir *üye numaralandırmadır*. Bunu bildiren sınıf, yapı, modül veya arabirimin bir üyesidir.

Üye numaralandırmalara, sınıfları, yapısı, modülü veya arabirimi içinde herhangi bir yerden erişilebilir. Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabit listesinin adını bu sınıf, yapı veya modülün adı ile nitelemesi gerekir. Kaynak dosyaya bir [Içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) açıklaması ekleyerek tam nitelikli adlar kullanma gereksinimini ortadan kaldırabilirsiniz.

Herhangi bir sınıf, yapı, modül veya arabirim dışında, ad alanı düzeyinde belirtilen bir sabit listesi, göründüğü ad alanının bir üyesidir.

Bir numaralandırma için *Bildirim bağlamı* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olmalıdır ve bir yordam olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Öznitelikleri bir numaralandırmaya bir bütün olarak uygulayabilir, ancak üyelerine tek tek atayabilirsiniz. Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur.

## <a name="data-type"></a>Veri Türü

`Enum` deyimin bir numaralandırmanın veri türünü bildirebilme. Her üye, numaralandırmanın veri türünü alır. `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`veya `UShort`belirtebilirsiniz.

Sabit listesi için `datatype` belirtmezseniz, her üye `initializer`veri türünü alır. Hem `datatype` hem de `initializer`belirtirseniz `initializer` veri türü `datatype`dönüştürülebilir olmalıdır. Ne `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak `Integer`.

## <a name="initializing-members"></a>Üyeler başlatılıyor

`Enum` deyimleri `memberlist`seçilen üyelerin içeriğini başlatabilir. Üyeye atanacak bir ifade sağlamak için `initializer` kullanırsınız.

Bir üye için `initializer` belirtmezseniz, Visual Basic sıfır (`memberlist`' de ilk `member`) veya hemen önceki `member`bir değere göre daha büyük bir değere başlatır.

Her bir `initializer` sağlanan ifade, herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve bu numaralandırmanın önceki bir üyesi dahil, zaten tanımlanmış olan sabit listesi üyeleri olabilir. Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.

`initializer`değişkenleri veya işlevleri kullanamazsınız. Ancak, `CByte` ve `CShort`gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz. `AscW`, derleme zamanında değerlendirilebilen bir sabit `String` veya `Char` bağımsız değişkeniyle çağırırsanız de kullanabilirsiniz.

Numaralandırmalar kayan nokta değerlerine sahip olamaz. Bir üyeye kayan nokta değeri atanırsa ve `Option Strict` on olarak ayarlandıysa, bir derleyici hatası oluşur. `Option Strict` kapalıysa, değer otomatik olarak `Enum` türüne dönüştürülür.

Bir üyenin değeri, temel alınan veri türü için izin verilen aralığı aşarsa veya herhangi bir üyeyi temel alınan veri türü tarafından izin verilen en yüksek değere başlattığınızda, derleyici bir hata bildirir.

## <a name="modifiers"></a>Değiştiriciler

Sınıf, yapı, modül ve arabirim üyesi numaralandırmalar, genel erişim için varsayılan. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Ad alanı üyesi numaralandırmalar arkadaş erişimi için varsayılan değer. Erişim düzeylerini herkese açık olarak ayarlayabilir, ancak özel veya korumalı olamaz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Tüm numaralandırma üyelerinin ortak erişimi vardır ve bunlar üzerinde herhangi bir erişim değiştiricilerini kullanamazsınız. Ancak, numaralandırmanın kendisi daha kısıtlı erişim düzeyine sahipse, belirtilen numaralandırma erişim düzeyi önceliklidir.

Varsayılan olarak, tüm numaralandırmalar türlerdir ve alanları sabittir. Bu nedenle, bir numaralandırma veya üyeleri bildirirken `Shared`, `Static`ve `ReadOnly` anahtar sözcükleri kullanılamaz.

## <a name="assigning-multiple-values"></a>Birden çok değer atama

Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder. `Enum` bildirimine <xref:System.FlagsAttribute> özniteliğini ekleyerek, bunun yerine sabit listesinin bir örneğine birden çok değer atayabilirsiniz. <xref:System.FlagsAttribute> özniteliği, numaralandırmanın bir bit alanı, yani bir bayrak kümesi olarak değerlendirilip değerlendirilmediğini belirtir. Bunlara *bit düzeyinde* numaralandırmalar denir.

<xref:System.FlagsAttribute> özniteliğini kullanarak bir numaralandırma bildirdiğinizde, değerler için 2, bu, 1, 2, 4, 8, 16, vb. üslerini kullanmanızı öneririz. Ayrıca "none" değerinin değeri 0 olan üyenin adı olması önerilir. Ek yönergeler için bkz. <xref:System.FlagsAttribute> ve <xref:System.Enum>.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Enum` deyimin nasıl kullanılacağını göstermektedir. Üyenin `Medium`değil `EggSizeEnum.Medium`olarak adlandırıldığına göz önünde bulunurlar.

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Örnek

Aşağıdaki örnekteki yöntem `Egg` sınıfının dışındadır. Bu nedenle, `EggSizeEnum` `Egg.EggSizeEnum`tam olarak nitelenir.

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, ilgili bir adlandırılmış sabit değer kümesini tanımlamak için `Enum` ifadesini kullanır. Bu durumda, değerler, bir veritabanı için veri girişi formları tasarlamayı seçebileceğiniz renklerdir.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, hem pozitif hem de negatif sayı içeren değerleri gösterir.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir numaralandırma `datatype` belirtmek için bir `As` yan tümcesi kullanılır.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bit düzeyinde numaralandırmanın nasıl kullanılacağını göstermektedir. Bit düzeyinde numaralandırma örneğine birden çok değer atanabilir. `Enum` bildirimi, numaralandırmanın bir dizi bayrak olarak değerlendirileceğini gösteren <xref:System.FlagsAttribute> özniteliğini içerir.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir numaralandırma boyunca yinelenir. Numaralandırmadaki üye adları dizisini almak için <xref:System.Enum.GetNames%2A> yöntemini kullanır ve üye değerleri dizisini almak için <xref:System.Enum.GetValues%2A>.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Sabitler ve Sabit Listeleri](../../../visual-basic/language-reference/constants-and-enumerations.md)
