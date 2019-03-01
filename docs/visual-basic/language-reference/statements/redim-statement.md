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
ms.openlocfilehash: 6ee30e885a08d3e8302d7b6083c1c65e525006c5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973437"
---
# <a name="redim-statement-visual-basic"></a>ReDim Deyimi (Visual Basic)
Bir dizi değişkeni için depolama alanını yeniden ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|----------|----------------|  
|`Preserve`|İsteğe bağlı. Değiştiricisi boyutu sadece son boyutu değiştirdiğinizde varolan dizedeki verileri korumak için kullanılır.|  
|`name`|Gerekli. Dizi değişkeni adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Gerekli. Yeniden tanımlanan dizinin her boyutunun sınırlarının listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `ReDim` bir veya daha fazla boyut zaten bildirilmiş bir dizinin boyutunu değiştirmek için deyimi. Uzun bir diziye sahip ve bazı alt öğeleri artık ihtiyacınız varsa `ReDim` dizi boyutu azaltarak belleği boşaltabilir. Daha fazla öğe diziniz gerekiyorsa diğer yandan, `ReDim` bunları ekleyebilirsiniz.  
  
 `ReDim` Deyimi yalnızca diziler için tasarlanmıştır. Skalerler (yalnızca tek bir değer içeren değişkenlerini), koleksiyonlar veya yapılar üzerinde geçerli değil. Bir değişken türünde bildirmeniz gerçekleştiriyorsanız `Array`, `ReDim` deyimi, yeni bir dizi oluşturmak için yeterli tür bilgisi yok.  
  
 Kullanabileceğiniz `ReDim` yalnızca yordamı düzeyinde. Bu nedenle, bildirimi bağlam değişkeni için bir yordam olmalıdır; bir kaynak dosyası, bir ad alanı, bir arabirim, bir sınıf, yapı, modül veya bir blok olamaz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Birden fazla değişken.** Aynı bildirim deyiminde birden fazla dizi değişkenlerini yeniden boyutlandırma ve belirtin `name` ve `boundlist` bölümleri her değişken için. Birden fazla değişken virgülle ayrılır.  
  
-   **Dizi sınırları.** Her giriş `boundlist` alt ve söz konusu boyut üst sınırları belirtebilirsiniz. Her zaman alt sınır olan 0 (sıfır). Değil (Bu üst sınırı yanı sıra bir durumdur) boyutun uzunluğu o boyut için en yüksek olası dizin değeri üst sınırıdır. Her boyutun dizini 0 ile üst sınır değeri arasında değişebilir.  
  
     İçindeki boyutların sayısına `boundlist` dizi boyutları (derece) özgün sayısı ile eşleşmelidir.  
  
-   **Veri türleri.** `ReDim` Deyimi bir diziye veya öğelerine veri türünü değiştirin.  
  
-   **Başlatma.** `ReDim` Deyimi, dizi öğeleri için yeni başlangıç değerleri sağlayamazsınız.  
  
-   **Boyut.** `ReDim` Deyimi (boyut sayısı) dizi boyut sayısını değiştirin.  
  
-   **Koruma ile yeniden boyutlandırma.** Kullanırsanız `Preserve`, sadece son boyutu dizinin yeniden boyutlandırabilirsiniz. Diğer her bir boyut için var olan bir dizi sınırı belirtmeniz gerekir.  
  
     Örneğin, yalnızca bir boyut diziniz varsa, boyut yeniden boyutlandırma ve yalnızca boyut ve son değiştirme çünkü hala dizinin tüm içerikleri korumak. İki veya daha fazla boyuta diziniz varsa kullanırsanız ancak sadece son boyutu boyutunu değiştirebileceğiniz `Preserve`.  
  
-   **özellikleri.** Kullanabileceğiniz `ReDim` değerler dizisi tutan bir özellikte.  
  
## <a name="behavior"></a>Davranış  
  
-   **Dizi değiştirme.** `ReDim` Varolan bir diziye serbest bırakır ve aynı dereceye yeni bir dizi oluşturur. Yeni bir dizi yayımlanan dizide dizi değişkenini değiştirir.  
  
-   **Başlatma olmadan korur.** Siz belirtmezseniz `Preserve`, `ReDim` kendi veri türü için varsayılan değer kullanarak yeni bir dizi öğelerini başlatır.  
  
-   **Koruma ile başlatma.** Belirtirseniz `Preserve`, Visual Basic mevcut bir diziden öğeleri için yeni bir diziye kopyalar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek dizinin var olan veri kaybı olmadan son boyutu dinamik bir dizinin boyutunu artırır ve ardından kısmi veri kaybıyla sonuçlanan boyuta azaltır. Son olarak, özgün değerine geri boyutunu azaltır ve tüm dizi öğeleri yeniden başlatır.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 `Dim` Deyimi üç boyut ile yeni bir dizi oluşturur. Her boyut için dizi dizini 0-10 aralığında, böylece her boyutun bağımlı 10 ile bildirilir. Aşağıdaki tartışmada boyutların için katman, satır ve sütun adlandırılır.  
  
 İlk `ReDim` değişkeni varolan dizide yerini alan yeni bir dizi oluşturur `intArray`. `ReDim` tüm öğeleri mevcut bir diziden yeni bir diziye kopyalar. Ayrıca her katman içindeki her bir satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunların 0 öğeleri başlatır (varsayılan değeri `Integer`, dizinin öğe türü).  
  
 İkinci `ReDim` başka bir yeni bir dizi oluşturur ve uygun tüm öğeleri kopyalar. Bununla birlikte beş sütun her katmanında her satır sonundan kaybolur. Bu sütunları kullanarak tamamlandıysa, bir sorun değildir. Uzun bir diziye boyutunu küçültmeyi artık gereksinim duymadığınız belleği boşaltmak.  
  
 Üçüncü `ReDim` başka bir yeni bir dizi oluşturur ve her katman içindeki her bir satırın son beş başka bir sütun kaldırır. Bu süre, var olan öğeleri kopyalamaz. Bu ifade, dizinin özgün boyutuna döner. Deyimi içermediği için `Preserve` özgün varsayılan değerlerine tüm dizi öğeleri ayarlar değiştiricisi.  
  
 Diğer örnekler için [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IndexOutOfRangeException>
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Erase Deyimi](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
