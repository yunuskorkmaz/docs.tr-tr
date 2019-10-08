---
title: Declare bildirimi (Visual Basic)
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
ms.openlocfilehash: e839fe14c360229fbe0350fd7878c7a844056e8b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005099"
---
# <a name="declare-statement"></a>Declare bildirimi

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

## <a name="parts"></a>Parçaya

|Sözleşme Dönemi|Tanım|
|---|---|
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [ortak](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [özel](../../../visual-basic/language-reference/modifiers/private.md)<br />- [korumalı arkadaş](../../language-reference/modifiers/protected-friend.md)<br />- [özel korumalı](../../language-reference/modifiers/private-protected.md)<br /><br /> [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|İsteğe bağlı. Karakter kümesi ve dosya arama bilgilerini belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (varsayılan)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|İsteğe bağlı, ancak `Sub` ya da `Function` görünmelidir. Dış yordamın bir değer döndürmediğini belirtir.|
|`Function`|İsteğe bağlı, ancak `Sub` ya da `Function` görünmelidir. Dış yordamın bir değer döndürdüğünü gösterir.|
|`name`|Gereklidir. Bu dış başvurunun adı. Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Gereklidir. Bir dış yordam içeren dış dosyayı (DLL veya kod kaynağı) tanımlayan `Lib` yan tümcesini tanıtır.|
|`libname`|Gereklidir. Belirtilen yordamı içeren dosyanın adı.|
|`Alias`|İsteğe bağlı. Bildirildiği yordamın, dosyası içinde `name` ' da belirtilen adla belirlenemediğini belirtir. @No__t-0 ' da kimliğini belirtirsiniz.|
|`aliasname`|@No__t-0 anahtar sözcüğünü kullanmanız gerekir. İki şekilde yordamı tanımlayan dize:<br /><br /> İçindeki yordamın, tırnak içindeki (`""`) giriş noktası adı<br /><br /> -veya-<br /><br /> Bir sayı işareti (`#`) ve ardından yordamın içindeki giriş noktasının sıra sayısını belirten bir tamsayı gelmelidir|
|`parameterlist`|Yordam parametreleri alırsa gereklidir. Bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|@No__t-0 belirtilmişse ve `Option Strict` `On` ise gereklidir. Yordamın döndürdüğü değerin veri türü.|

## <a name="remarks"></a>Açıklamalar

Bazen, bir dosyada (örneğin, bir DLL veya kod kaynağı gibi) tanımlanan bir yordamı projenizin dışında çağırmanız gerekir. Bunu yaptığınızda, Visual Basic derleyicisinin yordamın nerede olduğu, nasıl tanımlandığı, arama sırası ve dönüş türü ve kullandığı dize karakter kümesi gibi yordamı çağırması için gereken bilgilere erişimi yoktur. @No__t-0 ekstresi, bir dış yordama bir başvuru oluşturur ve bu gerekli bilgileri sağlar.

@No__t-0 ' i yalnızca modül düzeyinde kullanabilirsiniz. Bu, bir dış başvurunun *bildirim bağlamının* bir sınıf, yapı veya modül olması ve kaynak dosya, ad alanı, arabirim, yordam veya blok olması anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Dış başvurular varsayılan olarak [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.

## <a name="rules"></a>Kurallar

- **Özelliklerine.** Öznitelikleri bir dış başvuruya uygulayabilirsiniz. Uyguladığınız herhangi bir öznitelik, dış dosyada değil yalnızca projenizde etkilidir.

- **İlerine.** Dış yordamlar örtük olarak [paylaşılır](../../../visual-basic/language-reference/modifiers/shared.md). Dış başvuru bildirirken `Shared` anahtar sözcüğünü kullanamazsınız ve paylaşılan durumunu değiştiremezsiniz.

  Dış yordam, geçersiz kılma, arabirim üyeleri uygulama veya olayları işleme alanına katılamaz. Buna uygun olarak, bir @no__t 6 ifadesinde `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements` veya `Handles` anahtar sözcüğünü kullanamazsınız.

- **Dış yordam adı.** Bu dış başvuruya, dış dosya (`aliasname`) içinde yordamın giriş noktası adı ile aynı adı (`name`) vermeniz gerekmez. Giriş noktası adını belirtmek için `Alias` yan tümcesini kullanabilirsiniz. Bu, dış yordamın Visual Basic ayrılmış değiştirici veya bir değişken, yordam veya aynı kapsamda başka bir programlama öğesiyle aynı ada sahipse yararlı olabilir.

  > [!NOTE]
  > Çoğu dll 'deki giriş noktası adları büyük/küçük harfe duyarlıdır.

- **Dış yordam numarası.** Alternatif olarak, dış dosyanın dışarı aktarma tablosundaki giriş noktasının sıra sayısını belirtmek için `Alias` yan tümcesini kullanabilirsiniz. Bunu yapmak için, `aliasname` ' ı bir sayı işaretiyle (`#`) başlatın. Bu, dış yordam adındaki herhangi bir karaktere Visual Basic izin verilmiyorsa veya dış dosya yordamı bir ad olmadan dışarı aktardığında yararlı olabilir.

## <a name="data-type-rules"></a>Veri türü kuralları

- **Parametre veri türleri.** @No__t-0 `On` ise, her parametrenin veri türünü `parameterlist` ' de belirtmeniz gerekir. Bu, herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirimin adı olabilir. @No__t-0 içinde, her parametreye geçirilecek bağımsız değişkenin veri türünü belirtmek için bir `As` yan tümcesi kullanırsınız.

  > [!NOTE]
  > Dış yordam .NET Framework için yazılmadığından, veri türlerinin karşılık geldiği konusunda dikkatli olmanız gerekir. Örneğin, bir Visual Basic 6,0 yordamına bir `Integer` parametresiyle (Visual Basic 6,0 ' de 16 bit) bir dış başvuru bildirirseniz, karşılık gelen bağımsız değişkeni `Declare` ifadesinde `Short` olarak tanımlamalısınız, çünkü bu, içinde 16 bit tam sayı türüdür. Visual Basic. Benzer şekilde, `Long` Visual Basic 6,0 ' de farklı bir veri genişliğine sahiptir ve `Date` farklı şekilde uygulanır.

- **Dönüş veri türü.** Dış yordam bir `Function` ise ve `Option Strict` `On` ise, çağırma koduna döndürülen değerin veri türünü belirtmeniz gerekir. Bu, herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirimin adı olabilir.

  > [!NOTE]
  > Visual Basic Derleyicisi, veri türlerinizin dış yordamla uyumlu olduğunu doğrulamaz. Bir uyuşmazlık varsa, ortak dil çalışma zamanı çalışma zamanında bir <xref:System.Runtime.InteropServices.MarshalDirectiveException> özel durumu oluşturur.

- **Varsayılan veri türleri.** @No__t-0 `Off` ise ve `parameterlist` ' de bir parametrenin veri türünü belirtmezseniz, Visual Basic Derleyicisi ilgili bağımsız değişkeni [nesne veri türüne](../../../visual-basic/language-reference/data-types/object-data-type.md)dönüştürür. Benzer şekilde, `returntype` belirtmezseniz, derleyici dönüş veri türünü `Object` olacak şekilde alır.

  > [!NOTE]
  > Farklı bir platformda yazılmış olabilecek bir dış yordam ile ilgilenirken, veri türleri hakkında varsayımlar yapmak veya bunların varsayılan olmasına izin vermek tehlikeli olabilir. Varsa, her parametrenin ve dönüş değerinin veri türünü belirtmek çok daha güvenlidir. Bu, kodunuzun okunabilirliğini de artırır.

## <a name="behavior"></a>Davranış

- **Kapsam.** Dış başvuru, sınıf, yapı veya modül genelinde kapsamdadır.

- **Süre.** Dış başvuru, bildirildiği sınıf, yapı veya modülle aynı yaşam süresine sahiptir.

- **Dış yordam çağırma.** Bir dış yordamı, bir değeri döndürürse bir ifadede kullanarak veya bir değer döndürmezse bir [Call deyiminde](../../../visual-basic/language-reference/statements/call-statement.md) belirterek, bir `Function` veya `Sub` yordamını çağıran şekilde çağırabilirsiniz.

  Bağımsız değişkenleri, `Declare` ifadesinde `parameterlist` olarak belirtilen şekilde, dış yordama geçirin. Parametrelerin dış dosyada ilk olarak nasıl bildirildiği dikkate alma. Benzer şekilde, bir dönüş değeri varsa, `Declare` ifadesinde tam olarak `returntype` olarak belirtilen şekilde kullanın.

- **Karakter kümeleri.** @No__t-0 ' da, dış yordama çağrı yapıldığında dizeleri nasıl sıralayamaz Visual Basic belirtebilirsiniz. @No__t-0 değiştiricisi tüm dizeleri ANSI değerlerine göre sıralamak için Visual Basic yönlendirir ve `Unicode` değiştiricisi, bunu tüm dizeleri Unicode değerlerine göre sıralamak için yönlendirir. @No__t-0 değiştiricisi, Visual Basic dış @no__t başvuruya göre .NET Framework kurallara göre dizeleri sıralayamaz veya belirtilmişse `aliasname` ' ye yönlendirir. Varsayılan değer `Ansi` ' dır.

  `charsetmodifier` Ayrıca, Visual Basic dış yordamın dış dosyası içinde nasıl araması gerektiğini belirtir. `Ansi` ve `Unicode` her ikisi de arama sırasında adını değiştirmeden aramak için doğrudan Visual Basic. `Auto`, çalışma zamanı platformunun temel karakter kümesini belirlemede Visual Basic yönlendirir ve büyük olasılıkla dış yordam adını şu şekilde değiştirebilir:

  - Windows 95, Windows 98 veya Windows Millennium Edition gibi bir ANSI platformunda, önce ad değişikliğine sahip olmayan dış yordama bakmanız gerekir. Başarısız olursa, dış yordam adının sonuna "A" ekleyin ve tekrar arama yapın.

  - Windows NT, Windows 2000 veya Windows XP gibi bir Unicode platformunda, önce ad değişikliğine sahip olmayan dış yordama bakmanız gerekir. Başarısız olursa, dış yordam adının sonuna "W" ekleyin ve tekrar arama yapın.

- **Mekanizmadır.** Visual Basic, dış yordamları çözümlemek ve erişmek için .NET Framework *Platform çağırma* (PInvoke) mekanizmasını kullanır. @No__t-0 ve <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı bu mekanizmayı otomatik olarak kullanır ve herhangi bir PInvoke bilgisine ihtiyacınız yoktur. Daha fazla bilgi için bkz. [Izlenecek yol: Windows API 'Leri çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Dış yordam ortak dil çalışma zamanının (CLR) dışında çalışırsa, bu, yönetilmeyen bir *koddur*. Örneğin, bir Windows API işlevi veya bir COM yöntemi gibi bir yordamı çağırdığınızda, uygulamanızı güvenlik risklerine maruz kalabilirsiniz. Daha fazla bilgi için bkz. [yönetilmeyen kod Için güvenli kodlama yönergeleri](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, geçerli kullanıcı adını döndüren `Function` yordamına bir dış başvuru bildirir. Ardından, `getUser` yordamının bir parçası olarak `GetUserNameA` dış yordamını çağırır.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Örnek

@No__t-0, yönetilmeyen koddaki işlevleri kullanmanın alternatif bir yolunu sağlar. Aşağıdaki örnek, `Declare` açıklaması kullanmadan içeri aktarılan bir işlevi bildirir.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports ekstresi (.NET ad alanı ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf Işleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function ekstresi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ekstresi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call deyimleri](../../../visual-basic/language-reference/statements/call-statement.md)
- [İzlenecek yol: Windows API 'Lerini çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
