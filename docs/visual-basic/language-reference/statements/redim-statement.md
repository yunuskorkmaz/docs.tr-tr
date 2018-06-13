---
title: ReDim Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 9536ea8a6274e0b4a2589caf5aefa271a3567d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605400"
---
# <a name="redim-statement-visual-basic"></a>ReDim Deyimi (Visual Basic)
Depolama alanı için bir dizi değişkeni yeniden ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|----------|----------------|  
|`Preserve`|İsteğe bağlı. Yalnızca son boyut boyutunu değiştirdiğinizde, var olan dizideki verileri korumak için kullanılan değiştiricisi.|  
|`name`|Gerekli. Dizi değişkeni adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Gerekli. Yeniden tanımlanan dizinin her boyut sınırları listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `ReDim` dizi önceden tanımlanmış bir veya daha fazla boyutları boyutunu değiştirmek için deyimi. Uzun bir diziye sahip ve bazı öğeleri, artık ihtiyacınız varsa `ReDim` dizi boyutu azaltarak belleği boşaltmak. Daha fazla öğe dizinizi gerekirse diğer yandan, `ReDim` bunları ekleyebilirsiniz.  
  
 `ReDim` Deyimi yalnızca diziler için tasarlanmıştır. Skalerler (yalnızca tek bir değer içermesi değişkenler), koleksiyon veya yapıları geçerli değil. Türünde olması için bir değişken bildirirseniz unutmayın `Array`, `ReDim` deyimi, yeni bir dizi oluşturmak için yeterli türü bilgileri yok.  
  
 Kullanabileceğiniz `ReDim` yalnızca yordamı düzeyinde. Bu nedenle, değişken bildirimi bağlamının bir yordam olmalıdır; bir kaynak dosyası, bir ad alanı, bir arabirim, bir sınıf, bir yapı, bir modül veya bir blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Birden çok değişkenleri.** Aynı bildirimi deyiminde birden fazla dizi değişkenleri yeniden boyutlandırma ve belirtin `name` ve `boundlist` bölümleri her değişken için. Birden çok değişkenleri virgülle ayrılır.  
  
-   **Dizi sınırları.** Her giriş `boundlist` alt ve üst sınırlarını bu boyutun belirtebilirsiniz. Alt sınır olan her zaman 0 (sıfır). Bu boyut yok (olan üst sınır artı bir taneyi) boyutun uzunluğu için en yüksek olası dizin değeri üst sınırdır. Her boyut dizini 0'dan üst sınır değeri farklılık gösterebilir.  
  
     Boyutlar sayısı `boundlist` dizi boyutları (derece) özgün sayısı aynı olmalıdır.  
  
-   **Veri türleri.** `ReDim` Deyimi, bir dizi değişkeni veya öğelerini veri türünü değiştiremiyor.  
  
-   **başlatma.** `ReDim` Deyimi dizi öğeleri için yeni başlatma değerleri sağlayamazsınız.  
  
-   **RANK.** `ReDim` Deyimi dizi (dimensions sayısı) derecesini değiştiremiyor.  
  
-   **Koru ile yeniden boyutlandırma.** Kullanırsanız `Preserve`, yalnızca son boyut dizinin yeniden boyutlandırabilirsiniz. Diğer her bir boyut için mevcut dizisini bağlı belirtmeniz gerekir.  
  
     Örneğin, yalnızca bir boyut diziniz varsa, bu boyut yeniden boyutlandırabilir ve yalnızca boyut ve son değiştirme olduğundan hala dizi tüm içeriğini korumak. İki veya daha fazla boyutları diziniz varsa, kullanırsanız, ancak, yalnızca son boyut boyutunu değiştirebilirsiniz `Preserve`.  
  
-   **Özellikler.** Kullanabileceğiniz `ReDim` değerleri dizisi tutan bir özelliğe.  
  
## <a name="behavior"></a>Davranış  
  
-   **Dizi değiştirme.** `ReDim` Mevcut dizisini serbest bırakır ve aynı dereceye yeni bir dizi oluşturur. Yeni bir dizi dizi değişkeni yayımlanan dizisinde değiştirir.  
  
-   **Koruma olmadan başlatma.** Belirtmezseniz, `Preserve`, `ReDim` kendi veri türü için varsayılan değer kullanarak yeni bir dizi öğelerini başlatır.  
  
-   **Koru ile başlatma.** Belirtirseniz `Preserve`, Visual Basic varolan diziden öğeleri yeni diziye kopyalar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, mevcut verilerin herhangi biri dizisindeki kaybetmeden dinamik dizinin son boyutu boyutu artar ve kısmi veri kaybı boyutuyla azaltır. Son olarak, boyutu özgün değeri azaltır ve tüm dizi öğeleri yeniden başlatır.  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 `Dim` Deyim üç boyutlarla yeni bir dizi oluşturur. Dizi dizini her boyut için 0 ile 10 arası değişebilir şekilde her boyut sınır 10 değeri ile bildirildi. Aşağıdaki tartışmada boyutların için katman, satır ve sütun adlandırılır.  
  
 İlk `ReDim` değişkeninde varolan dizi yerini alacak yeni bir dizi oluşturur `intArray`. `ReDim` tüm öğeleri varolan diziden yeni diziye kopyalar. Ayrıca her katmandaki her satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunlar 0 öğelerinde başlatır (varsayılan değeri `Integer`, dizi öğesi türü olduğu).  
  
 İkinci `ReDim` başka bir yeni bir dizi oluşturur ve uyan tüm öğeler kopyalar. Ancak, beş sütun her katmandaki her satır sonundan kaybolur. Bu sütunları kullanarak tamamladığınızda bu bir sorun değildir. Uzun bir diziye boyutunun azaltılması, artık gereken belleği boşaltmak.  
  
 Üçüncü `ReDim` başka bir yeni bir dizi oluşturur ve her katmandaki her satır sonu başka bir beş sütun kaldırır. Bu süre, var olan öğeleri kopyalamaz. Bu bildirimi özgün boyutuna diziye döner. Deyim içermediği için `Preserve` değiştiricisi, bu ayarlar tüm dizi öğeleri özgün varsayılan değerlerine.  
  
 Ek örnekler için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IndexOutOfRangeException>  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Erase Deyimi](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
