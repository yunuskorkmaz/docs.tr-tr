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
ms.openlocfilehash: bc6949c7b52e87b7b39dd2690cac915a5f0d15aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="declare-statement"></a>Declare Deyimi
Bir dış dosyada uygulanan bir yordam için bir başvuru bildirir.  
  
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
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|İsteğe bağlı. Karakter kümesi ve dosya belirten bilgi arayın. Aşağıdakilerden biri olabilir:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (varsayılan)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Otomatik](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|İsteğe bağlı, ancak ya da `Sub` veya `Function` görünmesi gerekir. Dış yordamı bir değer döndürmüyor gösterir.|  
|`Function`|İsteğe bağlı, ancak ya da `Sub` veya `Function` görünmesi gerekir. Dış yordamı bir değer döndürür gösterir.|  
|`name`|Gerekli. Bu dış başvuru adı. Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Gerekli. Tanıtır bir `Lib` dış bir yordam içeren dış dosyası (DLL ya da kod kaynak) tanımlayan yan tümcesi.|  
|`libname`|Gerekli. Bildirilen yordamı içeren dosyanın adı.|  
|`Alias`|İsteğe bağlı. Bildirilen yordamı, dosyanın içinde belirtilen ada göre tanımlanamıyor gösterir `name`. Kendi Kimliği'nde belirttiğiniz `aliasname`.|  
|`aliasname`|Kullanırsanız, gerekli `Alias` anahtar sözcüğü. Yordamın iki yoldan biriyle tanımlayan dize:<br /><br /> Tırnak işareti içinde kendi dosya içinde yordam giriş noktası adı (`""`)<br /><br /> -veya-<br /><br /> Sayı işareti (`#`) dosya içinde yordam giriş noktası sıra sayısını belirten bir tamsayı ve ardından|  
|`parameterlist`|Yordamın kullandığı parametreler gereklidir. Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Gerekli olursa `Function` belirtilir ve `Option Strict` olan `On`. Yordam tarafından döndürülen değerin veri türü.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bazen projenizi dışında bir dosyayla (örneğin, DLL veya kod kaynağı) tanımlı bir yordam çağırma gerekir. Bunu yaparken, Visual Basic derleyici yordamı doğru çağırmak için gereken bilgileri için yordam bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü ve kullandığı dizeyi karakter kümesi gibi erişimi yok. `Declare` Deyimi dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 Kullanabileceğiniz `Declare` yalnızca modülü düzeyinde. Yani *bildirimi bağlam* bir dış başvuru sınıf, yapı veya modülü olmalı ve kaynak dosyasını, ad alanı, arabirim, yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Dış başvuran varsayılan [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Öznitelikler.** Bir dış başvuru öznitelikleri uygulayabilirsiniz. Uyguladığınız herhangi bir öznitelik etkisi projenizdeki yalnızca, dış dosyasında değil.  
  
-   **Değiştirici.** Dış yordamları olan örtük olarak [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md). Kullanamazsınız `Shared` bildirme bir dış başvuru ve paylaşılan durumu değiştirilemiyor, anahtar sözcük.  
  
     Dış bir yordam geçersiz kılma içinde katılmak, arabirim üyeleri uygulayan veya olayları işlemek. Buna göre kullanamazsınız `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, veya `Handles` in anahtar sözcüğü bir `Declare` deyimi.  
  
-   **Dış yordamın adı.** Bu dış başvuru aynı adı vermek gerekmez (içinde `name`) dış dosya içinde yordam giriş noktası adı (`aliasname`). Kullanabileceğiniz bir `Alias` yan tümcesini giriş noktası adı belirtin. Bu dış yordamı aynı kapsamda bir Visual Basic ayrılmış değiştirici veya bir değişkeni, yordam ya da herhangi bir programlama öğesi olarak aynı adı taşıyorsa yararlı olabilir.  
  
    > [!NOTE]
    >  Çoğu DLL'leri giriş noktası adları büyük/küçük harfe duyarlıdır.  
  
-   **Dış yordam numarası.** Alternatif olarak, kullanabileceğiniz bir `Alias` dışarı aktarma tablosu içindeki giriş noktası dış dosyasının sıra sayısını belirtmek için yan tümcesi. Bunu yapmak için başlamadan `aliasname` sayı işaretiyle (`#`). Visual Basic'te dış yordam adı herhangi bir karaktere izin verilmiyorsa veya dış dosya adı olmadan yordamı dışarı verirse bu yararlı olabilir.  
  
## <a name="data-type-rules"></a>Veri türü kuralları  
  
-   **Parametre veri türleri.** Varsa `Option Strict` olan `On`, her bir parametreyi veri türünü belirtmeniz gerekir `parameterlist`. Bu, herhangi bir veri türü ya da bir numaralandırma, yapısı, sınıf veya arabirim adı olabilir. İçinde `parameterlist`, kullandığınız bir `As` yan tümcesini her parametre için geçirilecek bağımsız değişkeninin veri türü belirtin.  
  
    > [!NOTE]
    >  Dış yordamı için .NET Framework yazılmadı varsa, veri türleri karşılık gelen ilgilenebilmek gerekir. Örneğin, bir dış başvuru bir Visual Basic 6.0 yordama bildirirseniz bir `Integer` parametre (Visual Basic 6.0 16 bit) karşılık gelen bağımsız değişken olarak tanımlamalıdır `Short` içinde `Declare` deyimi, 16 - olduğundan Visual Basic bit tamsayı yazın. Benzer şekilde, `Long` farklı veri genişliği Visual Basic 6. 0'dır ve `Date` farklı uygulanır.  
  
-   **Veri türü döndürür.** Dış yordam bir `Function` ve `Option Strict` olan `On`, çağrıyı yapan kod döndürülen değerin veri türünü belirtmeniz gerekir. Bu, herhangi bir veri türü ya da bir numaralandırma, yapısı, sınıf veya arabirim adı olabilir.  
  
    > [!NOTE]
    >  Visual Basic derleyici veri türlerinizi olanlar dış yordam ile uyumlu olduğunu doğrulamaz. Bir uyuşmazlık varsa, ortak dil çalışma zamanı oluşturan bir <xref:System.Runtime.InteropServices.MarshalDirectiveException> çalışma zamanında özel durum.  
  
-   **Varsayılan veri türleri.** Varsa `Option Strict` olan `Off` ve bir parametre veri türü belirtmeyin `parameterlist`, karşılık gelen bağımsız değişkeni Visual Basic derleyici dönüştürür [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md). Benzer şekilde, belirtmezseniz `returntype`, derleyici dönüş verisi türüne olması için geçen `Object`.  
  
    > [!NOTE]
    >  Farklı bir platformda yazılmış dış bir yordam ile çalışıyorsanız, veri türleri hakkında varsayımlar yapmak veya bunları varsayılan olarak izin vermek için tehlikeli demektir. Bunu varsa her parametre ve dönüş değeri veri türünü belirtmek daha güvenlidir. Bu da kodunuzun okunabilirliğini artırır.  
  
## <a name="behavior"></a>Davranış  
  
-   **Kapsamı.** Kapsam sınıfı, yapı veya modülü boyunca bir dış başvuru kullanılıyor.  
  
-   **Yaşam süresi.** Bir dış başvuru sınıf, yapı veya içinde bildirilmiş modülü olarak aynı yaşam süresi vardır.  
  
-   **Dış bir yordam çağırma.** Çağırmanız aynı şekilde dış bir yordam çağrısı bir `Function` veya `Sub` yordamı — bir değer döndürürse kullanarak bunu bir ifadede veya içinde belirterek bir [Call deyimi](../../../visual-basic/language-reference/statements/call-statement.md) bir değer döndürmezse.  
  
     Tam olarak belirtildiği gibi dış yordama bağımsız değişkenler geçirmek `parameterlist` içinde `Declare` deyimi. Parametreleri dış dosyasında başlangıçta nasıl bildirilen dikkate değil. Dönüş değeri varsa, benzer şekilde, tam olarak belirtildiği gibi kullanmak `returntype` içinde `Declare` deyimi.  
  
-   **Karakter kümeleri.** Belirleyebilirsiniz `charsetmodifier` dış yordamı çağırdığında Visual Basic dizeleri nasıl hazırlanacağını. `Ansi` Değiştiricisi Visual Basic ANSI değerleri, tüm dizeleri sıralama yönlendirir ve `Unicode` değiştiricisi Unicode değerleri tüm dizeleri sıralama için yönlendirir. `Auto` Değiştiricisi yönlendirir Visual Basic .NET Framework göre dizelerini sıralama kuralları dayalı üzerinde dış başvuru `name`, veya `aliasname` belirtilmişse. Varsayılan değer `Ansi` şeklindedir.  
  
     `charsetmodifier` Ayrıca nasıl Visual Basic dış yordam dış dosya içinde arama belirtir. `Ansi` ve `Unicode` her ikisi de arama sırasında adını değiştirmeden aramak için Visual Basic doğrudan. `Auto` Visual Basic çalışma zamanı platform temel karakter belirlemek ve büyük olasılıkla dış yordam adı şu şekilde değiştirmek için yönlendirir:  
  
    -   Windows 95, Windows 98 veya Windows Millennium Edition gibi bir ANSI platformunda ilk ad değişikliğe dış yordamını arayın. Başarısız olursa, "A" dış yordam adı sonuna ve arayın yeniden.  
  
    -   Windows NT, Windows 2000 veya Windows XP gibi bir Unicode platformunda ilk adı değişikliğe dış yordama bakın. Başarısız olursa, append dış yordamının sonuna "W" olarak adlandırın ve arayın yeniden.  
  
-   **Mekanizması.** Visual Basic kullanan .NET Framework *platform çağırma* çözümlemek ve dış yordamları erişmek için (PInvoke) mekanizması. `Declare` Deyimi ve <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfını hem bu düzenek otomatik olarak kullanın ve PInvoke bilgisi gerekmez. Daha fazla bilgi için bkz: [izlenecek yol: Windows API'larını çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Dış yordamı ortak dil çalışma zamanı dışında (CLR) çalıştırıyorsa, olan *yönetilmeyen kod*. Bu tür bir yordam, örneğin bir Win32 API işlev veya bir COM yöntemi çağırdığınızda uygulamanız güvenlik risklerine doğurabilir. Daha fazla bilgi için bkz: [güvenli kodlama yönergeleri yönetilmeyen kod için](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dış başvuru bildirir bir `Function` yordamı geçerli kullanıcı adını döndürür. Ardından bir dış yordam çağrıları `GetUserNameA` parçası olarak `getUser` yordamı.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 <xref:System.Runtime.InteropServices.DllImportAttribute> İşlevleri yönetilmeyen kod içinde kullanma, alternatif bir yol sağlar. Aşağıdaki örnekte bir içe aktarılan işlevi kullanmadan bildirir bir `Declare` deyimi.  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Call Deyimi](../../../visual-basic/language-reference/statements/call-statement.md)  
 [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
