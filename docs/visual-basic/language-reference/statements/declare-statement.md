---
title: Declare deyimi (Visual Basic)
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
ms.openlocfilehash: fbb7b4e118598157e2005469f89831df50de6576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638236"
---
# <a name="declare-statement"></a>Declare Deyimi
Bir dış dosya içinde uygulanmış yordama başvuru bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`attributelist`|İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Özel korumalı](../../language-reference/modifiers/private-protected.md)<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|İsteğe bağlı. Karakter kümesi ve dosya belirten bilgi arayın. Aşağıdakilerden biri olabilir:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (varsayılan)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|İsteğe bağlı, ancak ya da `Sub` veya `Function` yer almalıdır. Dış yordamın bir değer döndürmeyen gösterir.|  
|`Function`|İsteğe bağlı, ancak ya da `Sub` veya `Function` yer almalıdır. Dış yordamın bir değer döndürür gösterir.|  
|`name`|Gerekli. Bu dış başvurunun adı. Daha fazla bilgi için [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Gerekli. Tanıtır bir `Lib` bir dış yordam içeren dış dosyayı (DLL veya kod kaynağı) tanımlayan yan tümcesi.|  
|`libname`|Gerekli. Bildirilen yordam içeren dosyanın adı.|  
|`Alias`|İsteğe bağlı. Bildirilen yordamı kendi dosyası içinde belirtilen adla tanımlanamıyor gösterir `name`. Kendi Kimliği'nde belirttiğiniz `aliasname`.|  
|`aliasname`|İfadesini kullanıyorsanız gereklidir `Alias` anahtar sözcüğü. İki yoldan biriyle yordamı tanımlayan dize:<br /><br /> Tırnak içinde bir dosya içinde yordam giriş noktası adı (`""`)<br /><br /> -veya-<br /><br /> Sayı işareti (`#`), dosya içinde yordam giriş noktasının bir sıra numarası belirten bir tamsayı ardından|  
|`parameterlist`|Yordamın kullandığı parametreler gereklidir. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Gerekli if `Function` belirtilir ve `Option Strict` olduğu `On`. Yordamın döndürdüğü değerin veri türü.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı durumlarda (örneğin, bir DLL veya kod kaynağı) bir dosyayı projenizin dışında tanımlı bir yordam çağırma gerekir. Bunu yaptığınızda, Visual Basic Derleyicisi yordamı bulunduğu, nasıl tanımlandığını, kendi arama sırası ve dönüş türü ve kullandığı dize karakter kümesi gibi yordamı doğru şekilde çağırmak gereken bilgilere erişim yok. `Declare` Deyimi bir dış yordam bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 Kullanabileceğiniz `Declare` yalnızca Modül düzeyinde. Başka bir deyişle *bildirim içeriğinin* dış başvuru sınıfı, yapısını veya modülünü olmalıdır ve bir kaynak dosyası, ad alanı, arabirim, yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Dış başvuruları için varsayılan [genel](../../../visual-basic/language-reference/modifiers/public.md) erişim. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
- **Öznitelikleri.** Bir dış başvuru öznitelikleri uygulayabilirsiniz. Uyguladığınız herhangi bir öznitelik etkisi, projenizdeki yalnızca, dış dosya içinde değil.  
  
- **Değiştiriciler.** Dış yordamları olan örtük olarak [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md). Kullanamazsınız `Shared` bildirme dış başvuru ve paylaşılan durumu değiştirilemiyor, anahtar sözcüğü.  
  
     Bir dış yordam geçersiz kılma olarak katılmak, arabirim üyeleri uygulamak veya olaylarını işleme. Buna kullanamazsınız `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, veya `Handles` anahtar sözcüğü bir `Declare` deyimi.  
  
- **Dış yordamın adı.** Bu dış başvurunun aynı adı verin gerekmez (içinde `name`), dış dosya içinde yordam giriş noktası adı (`aliasname`). Kullanabileceğiniz bir `Alias` yan giriş noktası adını belirtin. Bu, dış yordam aynı kapsam içinde bir Visual Basic ayrılmış değiştiricisi veya bir değişken, yordam veya herhangi bir programlama öğesi aynı ada sahipse yararlı olabilir.  
  
    > [!NOTE]
    >  Çoğu dll giriş noktası adları büyük/küçük harfe duyarlıdır.  
  
- **Dış yordam numarası.** Alternatif olarak, bir `Alias` yan dış dosyasının dışarı aktarma tablo içindeki giriş noktasının bir sıra numarası belirtin. Bunu yapmak için başlamadan `aliasname` sayı işaretiyle (`#`). Dış yordam adının herhangi bir karakterle Visual Basic'te izin verilmiyorsa veya dış dosya adı olmayan bir yordam dışarı aktarır. Bu yararlı olabilir.  
  
## <a name="data-type-rules"></a>Veri türü kuralları  
  
- **Parametre veri türleri.** Varsa `Option Strict` olduğu `On`, her parametre veri türünü belirtmeniz gerekir `parameterlist`. Bu, herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını olabilir. İçinde `parameterlist`, kullandığınız bir `As` yan her parametreye geçirilecek bağımsız değişken veri türünü belirtin.  
  
    > [!NOTE]
    >  .NET Framework için dış yordam yazılamadı ise, veri türleri karşılık gelen ilgileniriz gerekir. Örneğin, bir dış başvuru içeren bir Visual Basic 6.0 yordamı bildirirseniz bir `Integer` parametre (Visual Basic 6.0 16 bit) karşılık gelen bağımsız değişken olarak belirlemeniz gerekir `Short` içinde `Declare` deyimi, 16 - olduğundan Visual Basic'te bit tamsayı türü. Benzer şekilde, `Long` Visual Basic 6. 0'da, farklı veri genişliği sahiptir ve `Date` farklı şekilde uygulanır.  
  
- **Veri türü döndürür.** Dış yordam bir `Function` ve `Option Strict` olduğu `On`, çağrıldığı koda döndürülen değer veri türünü belirtmeniz gerekir. Bu, herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını olabilir.  
  
    > [!NOTE]
    >  Visual Basic Derleyicisi, veri türleri bu dış yordam ile uyumlu olduğunu doğrulamaz. Bir uyuşmazlık varsa, ortak dil çalışma zamanı oluşturur bir <xref:System.Runtime.InteropServices.MarshalDirectiveException> çalışma zamanında özel durum.  
  
- **Varsayılan veri türleri.** Varsa `Option Strict` olduğu `Off` ve veri türü bir parametre belirtmezseniz `parameterlist`, karşılık gelen bağımsız değişkeni Visual Basic Derleyicisi dönüştürür [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md). Benzer şekilde, siz belirtmezseniz `returntype`, derleyici dönüş veri türünün olmasını alan `Object`.  
  
    > [!NOTE]
    >  Farklı bir platformda yazılmış bir dış yordam ile çalışıyorsanız, veri türleri hakkında varsayımlar veya varsayılan olarak izin vermek tehlikeli olmasıdır. Varsa her parametre ve dönüş değerinin veri türü belirtmek daha güvenlidir. Bu da kodunuzun okunabilirliği geliştirir.  
  
## <a name="behavior"></a>Davranış  
  
- **Kapsam.** Bir dış, sınıf, yapı veya modül kapsamdadır başvurudur.  
  
- **Yaşam süresi.** Dış başvuru sınıfı, yapı veya modül içinde bildirildiği olarak aynı kullanım ömrü vardır.  
  
- **Dış bir yordam çağırma.** Bir dış yordam çağrısı aynı şekilde çağırmak bir `Function` veya `Sub` yordamı — bir değer döndürürse, bir ifadede kullanarak veya içinde belirterek bir [Call deyimi](../../../visual-basic/language-reference/statements/call-statement.md) bir değer döndürmezse.  
  
     Tam olarak belirtilen dış yordam bağımsız değişkenleri geçirmek `parameterlist` içinde `Declare` deyimi. Parametreleri dış dosyasında başlangıçta nasıl bildirilen dikkate almaz. Dönüş değeri varsa, benzer şekilde, tam olarak belirtilen kullanmaya `returntype` içinde `Declare` deyimi.  
  
- **Karakter kümeleri.** Belirleyebilirsiniz `charsetmodifier` dış yordam çağırdığında, Visual Basic dizeleri nasıl sıralamanız. `Ansi` Değiştiricisi, Visual Basic tüm dizeleri ANSI değerleri olarak sıralaması yönlendirir ve `Unicode` değiştiricisi tüm dizeleri Unicode değerleri olarak sıralaması için yönlendirir. `Auto` Değiştiricisi, Visual Basic .NET Framework göre dizelerini sıralama kurallarını temel üzerinde dış başvuru yönlendirir `name`, veya `aliasname` belirtilmişse. Varsayılan değer `Ansi` şeklindedir.  
  
     `charsetmodifier` Ayrıca, Visual Basic dış yordam, dış dosya içinde yukarı nasıl görünmelidir belirtir. `Ansi` ve `Unicode` hem de Visual Basic, arama sırasında adını değiştirmeden aramak için doğrudan. `Auto` Visual Basic çalışma zamanı platformunun temel karakter kümesini belirlemek ve büyük olasılıkla dış yordam adının şu şekilde değiştirin yönlendirir:  
  
    - Windows 95, Windows 98 veya Windows Me gibi bir ANSI platformunda dış yordam adının herhangi bir değişiklik olmadan önce arayın. Bu başarısız olursa, "A" dış yordam adının sonuna ve arayın yeniden.  
  
    - Windows NT, Windows 2000 veya Windows XP gibi bir Unicode platformunda dış yordam adının herhangi bir değişiklik olmadan önce arayın. Bu başarısız olursa ekleme dış yordamın sonuna "W" olarak adlandırın ve arayın yeniden.  
  
- **Mekanizması.** Visual Basic .NET Framework kullanan *platform çağırma* gidermek ve dış yordamları erişmek için (PInvoke) mekanizması. `Declare` Deyimi ve <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı hem de bu mekanizma otomatik olarak kullanın ve bilgisine sahip PInvoke gerekmez. Daha fazla bilgi için [izlenecek yol: Windows API'larını çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Dış yordam ortak dil çalışma zamanı dışında (CLR) çalıştırıyorsa olduğu *yönetilmeyen kod*. Bu yordamı, örneğin, bir Windows API işlevi ya da bir COM yöntemi çağırdığınızda, uygulamanıza güvenlik risklerini doğurabilir. Daha fazla bilgi için [güvenli kodlama kılavuzları yönetilmeyen kod için](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dış başvuru bildirir. bir `Function` geçerli kullanıcı adını döndüren yordam. Ardından bir dış yordam çağrıları `GetUserNameA` parçası olarak `getUser` yordamı.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="example"></a>Örnek  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Yönetilmeyen kodda işlevleri'ni kullanarak, alternatif bir yolunu sağlar. Aşağıdaki örnek kullanmadan içeri aktarılan bir işlev bildirir. bir `Declare` deyimi.  
  
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
