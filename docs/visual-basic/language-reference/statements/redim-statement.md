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
ms.openlocfilehash: a9384ba118df2a84fbd2581e6a8bacb58e41ddcc
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582079"
---
# <a name="redim-statement-visual-basic"></a>ReDim Deyimi (Visual Basic)
, Bir dizi değişkeni için depolama alanını yeniden konumlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|----------|----------------|  
|`Preserve`|İsteğe bağlı. Yalnızca son boyutun boyutunu değiştirirken mevcut dizideki verileri korumak için kullanılan değiştirici.|  
|`name`|Gerekli. Dizi değişkeninin adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Gerekli. Yeniden tanımlanmış dizinin her boyutunun sınırları listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Önceden tanımlanmış bir dizinin bir veya daha fazla boyutunun boyutunu değiştirmek için `ReDim` ifadesini kullanabilirsiniz. Büyük bir diziniz varsa ve öğelerin bazılarını artık gerekmiyorsa, `ReDim` dizi boyutunu azaltarak belleği serbest bırakabilirsiniz. Öte yandan, dizide daha fazla öğe gerekiyorsa `ReDim` bunları ekleyebilir.  
  
 @No__t_0 deyimleri yalnızca diziler için tasarlanmıştır. Yapı değerleri (yalnızca tek bir değer içeren değişkenler), koleksiyonlar veya yapılar üzerinde geçerli değildir. @No__t_0 türünde olacak bir değişken bildirirseniz, `ReDim` deyimin yeni diziyi oluşturmak için yeterli tür bilgilerine sahip olmadığını unutmayın.  
  
 Yalnızca yordam düzeyinde `ReDim` kullanabilirsiniz. Bu nedenle, değişken için bildirim bağlamı bir yordam olmalıdır; Kaynak dosya, ad alanı, arabirim, sınıf, yapı, modül veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Birden çok değişken.** Aynı bildirim deyimindeki birkaç dizi değişkenini yeniden boyutlandırabilir ve her değişken için `name` ve `boundlist` parçalarını belirtebilirsiniz. Birden çok değişken virgülle ayrılır.  
  
- **Dizi sınırları.** @No__t_0 içindeki her giriş, bu boyutun alt ve üst sınırlarını belirtebilir. Alt sınır her zaman 0 (sıfır) olur. Üst sınır, boyutun uzunluğunu değil, bu boyut için mümkün olan en yüksek dizin değeridir (üst sınır artı bir değerdir). Her boyutun dizini, üst sınır değeri ile 0 arasında değişebilir.  
  
     @No__t_0 boyut sayısı, dizinin orijinal boyut sayısıyla (derece) eşleşmelidir.  
  
- **Veri türleri.** @No__t_0 ifade, bir dizi değişkeninin veya öğelerinin veri türünü değiştiremiyor.  
  
- **Başlatılmasında.** @No__t_0 deyimin dizi öğeleri için yeni başlatma değerleri sağlayamaz.  
  
- **Sırası.** @No__t_0 ifade, dizinin derecesini (boyut sayısı) değiştiremiyor.  
  
- **Preserve ile yeniden boyutlandırma.** @No__t_0 kullanırsanız, yalnızca dizinin son boyutunu yeniden boyutlandırabilirsiniz. Diğer tüm boyutlar için, var olan dizinin bir ilişkisini belirtmeniz gerekir.  
  
     Örneğin, dizide yalnızca bir boyut varsa, en son ve yalnızca boyutu değiştirdiğiniz için bu boyutu yeniden boyutlandırabilir ve dizinin tüm içeriğini koruyabilirsiniz. Ancak, dizide iki veya daha fazla boyut varsa, `Preserve` kullanırsanız yalnızca son boyutun boyutunu değiştirebilirsiniz.  
  
- **Özelliklerinin.** @No__t_0, bir değer dizisini tutan bir özellik üzerinde kullanabilirsiniz.  
  
## <a name="behavior"></a>Davranış  
  
- **Dizi değiştirme.** `ReDim` var olan diziyi serbest bırakır ve aynı dereceye sahip yeni bir dizi oluşturur. Yeni dizi, dizi değişkeninde yayınlanan dizinin yerini alır.  
  
- **Preserve olmadan başlatma.** @No__t_0 belirtmezseniz, `ReDim` veri türleri için varsayılan değeri kullanarak yeni dizinin öğelerini başlatır.  
  
- **Preserve ile başlatma.** @No__t_0 belirtirseniz, öğeleri varolan diziden yeni diziye kopyalar Visual Basic.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizideki mevcut verileri kaybetmeden dinamik bir dizinin en son boyutunun boyutunu artırır ve sonra boyutu kısmi veri kaybıyla azaltır. Son olarak, boyutu özgün değerine geri düşürür ve tüm dizi öğelerini yeniden başlatır.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 @No__t_0 deyimleri, üç boyutlu yeni bir dizi oluşturur. Her boyut 10 ' un bir bağı ile bildirildiği için her boyutun dizi dizini 0 ile 10 arasında değişebilir. Aşağıdaki tartışmada, üç boyut katman, satır ve sütun olarak adlandırılır.  
  
 İlk `ReDim`, değişken `intArray` var olan dizinin yerini alan yeni bir dizi oluşturur. `ReDim` varolan dizideki tüm öğeleri yeni diziye kopyalar. Ayrıca, her katmandaki her satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunlardaki öğeleri 0 ' a (dizinin öğe türü olan `Integer` varsayılan değeri) başlatır.  
  
 İkinci `ReDim` başka bir yeni dizi oluşturur ve uygun olan tüm öğeleri kopyalar. Ancak, her katmandaki her satırın sonundan beş sütun kaybolur. Bu sütunları kullanmayı bitirdiğinizde bu bir sorun değildir. Büyük bir dizinin boyutunu azaltmak artık ihtiyaç duymayacak belleği serbest bırakabilirsiniz.  
  
 Üçüncü `ReDim` başka bir yeni dizi oluşturur ve her katmandaki her satırın sonundan başka beş sütunu kaldırır. Bu kez, var olan herhangi bir öğeyi kopyalamaz. Bu ifade, diziyi özgün boyutuna geri döndürür. Deyimin `Preserve` değiştiricisini içermediğinden, tüm dizi öğelerini özgün varsayılan değerlerine ayarlar.  
  
 Daha fazla örnek için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IndexOutOfRangeException>
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Erase Deyimi](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
