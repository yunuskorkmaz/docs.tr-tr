---
title: Declare Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 48a36e3ecdef40810ea7a3194e85b5b646154331
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354085"
---
# <a name="declare-statement"></a>Declare Deyimi

Dış dosyada uygulanan bir yordama başvuru bildirir.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [özel](../../../visual-basic/language-reference/modifiers/private.md)<br />- [korumalı arkadaş](../../language-reference/modifiers/protected-friend.md)<br />- [özel korumalı](../../language-reference/modifiers/private-protected.md)<br /><br /> [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|İsteğe bağlı. Karakter kümesi ve dosya arama bilgilerini belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (varsayılan)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />[otomatik](../../../visual-basic/language-reference/modifiers/auto.md) -   |
|`Sub`|İsteğe bağlı, ancak `Sub` ya da `Function` görünmelidir. Dış yordamın bir değer döndürmediğini belirtir.|
|`Function`|İsteğe bağlı, ancak `Sub` ya da `Function` görünmelidir. Dış yordamın bir değer döndürdüğünü gösterir.|
|`name`|Gerekli. Bu dış başvurunun adı. Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Gerekli. Bir dış yordam içeren dış dosyayı (DLL veya kod kaynağı) tanımlayan bir `Lib` yan tümcesi tanıtır.|
|`libname`|Gerekli. Belirtilen yordamı içeren dosyanın adı.|
|`Alias`|İsteğe bağlı. Bildirildiği yordamın, `name`içinde belirtilen ad ile dosyasında belirlenemediğini belirtir. `aliasname`kimliğini belirtin.|
|`aliasname`|`Alias` anahtar sözcüğünü kullanmanız gerekir. İki şekilde yordamı tanımlayan dize:<br /><br /> İçindeki yordamın giriş noktası adı, tırnak içinde (`""`)<br /><br /> veya<br /><br /> Bir sayı işareti (`#`) ve ardından yordamın giriş noktasının sıra sayısını belirten bir tamsayı.|
|`parameterlist`|Yordam parametreleri alırsa gereklidir. Bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|`Function` belirtilirse ve `Option Strict` `On`gerekir. Yordamın döndürdüğü değerin veri türü.|

## <a name="remarks"></a>Açıklamalar

Bazen, bir dosyada (örneğin, bir DLL veya kod kaynağı gibi) tanımlanan bir yordamı projenizin dışında çağırmanız gerekir. Bunu yaptığınızda, Visual Basic derleyicisinin yordamın nerede olduğu, nasıl tanımlandığı, arama sırası ve dönüş türü ve kullandığı dize karakter kümesi gibi yordamı çağırması için gereken bilgilere erişimi yoktur. `Declare` deyimleri, bir dış yordama yönelik bir başvuru oluşturur ve bu gerekli bilgileri sağlar.

Yalnızca modül düzeyinde `Declare` kullanabilirsiniz. Bu, bir dış başvurunun *bildirim bağlamının* bir sınıf, yapı veya modül olması ve kaynak dosya, ad alanı, arabirim, yordam veya blok olması anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Dış başvurular varsayılan olarak [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

## <a name="rules"></a>Kurallar

- **Özelliklerine.** Öznitelikleri bir dış başvuruya uygulayabilirsiniz. Uyguladığınız herhangi bir öznitelik, dış dosyada değil yalnızca projenizde etkilidir.

- **İlerine.** Dış yordamlar örtük olarak [paylaşılır](../../../visual-basic/language-reference/modifiers/shared.md). Dış başvuru bildirirken `Shared` anahtar sözcüğünü kullanamazsınız ve paylaşılan durumunu değiştiremezsiniz.

  Dış yordam, geçersiz kılma, arabirim üyeleri uygulama veya olayları işleme alanına katılamaz. Buna uygun olarak, bir `Implements`deyimindeki `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Handles` veya `Declare` anahtar sözcüğünü kullanamazsınız.

- **Dış yordam adı.** Bu dış başvuruya, dış dosya (`aliasname`) içinde yordamın giriş noktası adı ile aynı adı (`name`) vermeniz gerekmez. Giriş noktası adını belirtmek için bir `Alias` yan tümcesi kullanabilirsiniz. Bu, dış yordamın Visual Basic ayrılmış değiştirici veya bir değişken, yordam veya aynı kapsamda başka bir programlama öğesiyle aynı ada sahipse yararlı olabilir.

  > [!NOTE]
  > Çoğu dll 'deki giriş noktası adları büyük/küçük harfe duyarlıdır.

- **Dış yordam numarası.** Alternatif olarak, dış dosyanın dışarı aktarma tablosundaki giriş noktasının sıra sayısını belirtmek için bir `Alias` yan tümcesi kullanabilirsiniz. Bunu yapmak için `aliasname` bir sayı işaretiyle (`#`) başlarsınız. Bu, dış yordam adındaki herhangi bir karaktere Visual Basic izin verilmiyorsa veya dış dosya yordamı bir ad olmadan dışarı aktardığında yararlı olabilir.

## <a name="data-type-rules"></a>Veri türü kuralları

- **Parametre veri türleri.** `Option Strict` `On`, `parameterlist`her parametrenin veri türünü belirtmeniz gerekir. Bu, herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirimin adı olabilir. `parameterlist`içinde, her parametreye geçirilecek bağımsız değişkenin veri türünü belirtmek için bir `As` yan tümcesi kullanın.

  > [!NOTE]
  > Dış yordam .NET Framework için yazılmadığından, veri türlerinin karşılık geldiği konusunda dikkatli olmanız gerekir. Örneğin, bir Visual Basic 6,0 yordamına bir `Integer` parametresiyle (Visual Basic 6,0 ' de 16 bit) bir dış başvuru bildirirseniz, `Declare` ifadesinde 16 bit tamsayı türü olduğundan karşılık gelen bağımsız değişkeni Visual Basic deyimindeki `Short` olarak tanımlamalısınız. Benzer şekilde, `Long` Visual Basic 6,0 ' de farklı bir veri genişliğine sahiptir ve `Date` farklı şekilde uygulanır.

- **Dönüş veri türü.** Dış yordam bir `Function` ve `Option Strict` `On`ise, çağırma koduna döndürülen değerin veri türünü belirtmeniz gerekir. Bu, herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirimin adı olabilir.

  > [!NOTE]
  > Visual Basic Derleyicisi, veri türlerinizin dış yordamla uyumlu olduğunu doğrulamaz. Bir uyuşmazlık varsa, ortak dil çalışma zamanı çalışma zamanında bir <xref:System.Runtime.InteropServices.MarshalDirectiveException> özel durumu oluşturur.

- **Varsayılan veri türleri.** `Option Strict` `Off` ve `parameterlist`bir parametrenin veri türünü belirtmezseniz, Visual Basic Derleyicisi ilgili bağımsız değişkeni [nesne veri türüne](../../../visual-basic/language-reference/data-types/object-data-type.md)dönüştürür. Benzer şekilde, `returntype`belirtmezseniz, derleyici döndürülen veri türünü `Object`olarak alır.

  > [!NOTE]
  > Farklı bir platformda yazılmış olabilecek bir dış yordam ile ilgilenirken, veri türleri hakkında varsayımlar yapmak veya bunların varsayılan olmasına izin vermek tehlikeli olabilir. Varsa, her parametrenin ve dönüş değerinin veri türünü belirtmek çok daha güvenlidir. Bu, kodunuzun okunabilirliğini de artırır.

## <a name="behavior"></a>Davranış

- **Kapsam.** Dış başvuru, sınıf, yapı veya modül genelinde kapsamdadır.

- **Süre.** Dış başvuru, bildirildiği sınıf, yapı veya modülle aynı yaşam süresine sahiptir.

- **Dış yordam çağırma.** Bir dış yordamı, bir değeri döndürürse bir ifadede kullanarak veya bir değer döndürmezse bir [Call deyiminde](../../../visual-basic/language-reference/statements/call-statement.md) belirterek, bir `Function` veya `Sub` yordamını çağıran şekilde çağırabilirsiniz.

  Bağımsız değişkenleri, `Declare` bildiriminde `parameterlist` tarafından belirtilen şekilde dış yordama geçirirsiniz. Parametrelerin dış dosyada ilk olarak nasıl bildirildiği dikkate alma. Benzer şekilde, bir dönüş değeri varsa, tam olarak `Declare` deyimindeki `returntype` tarafından belirtilen şekilde kullanın.

- **Karakter kümeleri.** Dış yordamı çağırdığında Visual Basic dizelerin nasıl sıralaması gerektiğini `charsetmodifier` belirtebilirsiniz. `Ansi` değiştirici, tüm dizeleri ANSI değerlerine göre sıralamak için Visual Basic yönlendirir ve `Unicode` değiştirici onu tüm dizeleri Unicode değerlerine göre sıralamak için yönlendirir. `Auto` değiştirici, Visual Basic dış `name`başvuruya göre .NET Framework kurallara göre dizeleri sıralayamaz veya belirtilmişse `aliasname`. Varsayılan değer `Ansi` şeklindedir.

  `charsetmodifier` Ayrıca, Visual Basic dış yordamın dış dosyası içinde nasıl araması gerektiğini belirtir. `Ansi` ve `Unicode`, arama sırasında adını değiştirmeden aramak için doğrudan Visual Basic. `Auto`, çalışma zamanı platformunun temel karakter kümesini belirlemede Visual Basic yönlendirir ve büyük olasılıkla dış yordam adını şu şekilde değiştirebilir:

  - Windows 95, Windows 98 veya Windows Millennium Edition gibi bir ANSI platformunda, önce ad değişikliğine sahip olmayan dış yordama bakmanız gerekir. Başarısız olursa, dış yordam adının sonuna "A" ekleyin ve tekrar arama yapın.

  - Windows NT, Windows 2000 veya Windows XP gibi bir Unicode platformunda, önce ad değişikliğine sahip olmayan dış yordama bakmanız gerekir. Başarısız olursa, dış yordam adının sonuna "W" ekleyin ve tekrar arama yapın.

- **Mekanizmadır.** Visual Basic, dış yordamları çözümlemek ve erişmek için .NET Framework *Platform çağırma* (PInvoke) mekanizmasını kullanır. `Declare` ve <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı her ikisi de bu mekanizmayı otomatik olarak kullanır ve herhangi bir PInvoke bilgisine ihtiyacınız yoktur. Daha fazla bilgi için bkz. [Izlenecek yol: Windows API 'Leri çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Dış yordam ortak dil çalışma zamanının (CLR) dışında çalışırsa, bu, yönetilmeyen bir *koddur*. Örneğin, bir Windows API işlevi veya bir COM yöntemi gibi bir yordamı çağırdığınızda, uygulamanızı güvenlik risklerine maruz kalabilirsiniz. Daha fazla bilgi için bkz. [yönetilmeyen kod Için güvenli kodlama yönergeleri](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, geçerli kullanıcı adını döndüren `Function` yordamına bir dış başvuru bildirir. Ardından, `getUser` yordamının bir parçası olarak `GetUserNameA` dış yordamı çağırır.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Örnek

<xref:System.Runtime.InteropServices.DllImportAttribute> yönetilmeyen koddaki işlevleri kullanmanın alternatif bir yolunu sağlar. Aşağıdaki örnek, `Declare` bir ifade kullanmadan içeri aktarılan bir işlevi bildirir.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call Deyimi](../../../visual-basic/language-reference/statements/call-statement.md)
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
