---
title: ReDim Deyimi
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
ms.openlocfilehash: 17bc806f2e92c61f1dd7425de40b1a68f926a583
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872028"
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
|`name`|Gereklidir. Dizi değişkeninin adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Gereklidir. Yeniden tanımlanmış dizinin her boyutunun sınırları listesi.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ReDim`Önceden tanımlanmış bir dizinin bir veya daha fazla boyutunun boyutunu değiştirmek için ifadesini kullanabilirsiniz. Büyük bir diziniz varsa ve bazı öğeleri artık gerekmiyorsa, `ReDim` dizi boyutunu azaltarak belleği serbest bırakabilirsiniz. Öte yandan, dizide daha fazla öğe gerekiyorsa, `ReDim` bunları ekleyebilir.  
  
 `ReDim`İfade yalnızca diziler için tasarlanmıştır. Yapı değerleri (yalnızca tek bir değer içeren değişkenler), koleksiyonlar veya yapılar üzerinde geçerli değildir. Türünde bir değişken bildirirseniz `Array` , `ReDim` deyimin yeni diziyi oluşturmak için yeterli tür bilgilerine sahip olmadığını unutmayın.  
  
 `ReDim`Yalnızca yordam düzeyinde kullanabilirsiniz. Bu nedenle, değişken için bildirim bağlamı bir yordam olmalıdır; Kaynak dosya, ad alanı, arabirim, sınıf, yapı, modül veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Birden çok değişken.** Aynı bildirim deyimindeki birkaç dizi değişkenini yeniden boyutlandırabilir ve `name` `boundlist` her değişken için ve parçalarını belirtebilirsiniz. Birden çok değişken virgülle ayrılır.  
  
- **Dizi sınırları.** İçindeki her giriş `boundlist` , bu boyutun alt ve üst sınırlarını belirtebilir. Alt sınır her zaman 0 (sıfır) olur. Üst sınır, boyutun uzunluğunu değil, bu boyut için mümkün olan en yüksek dizin değeridir (üst sınır artı bir değerdir). Her boyutun dizini, üst sınır değeri ile 0 arasında değişebilir.  
  
     İçindeki boyutların sayısı, `boundlist` dizinin orijinal boyut (derece) sayısıyla eşleşmelidir.  
  
- **Veri türleri.** `ReDim`İfade, bir dizi değişkeninin veya öğelerinin veri türünü değiştiremiyor.  
  
- **Başlatılmasında.** `ReDim`İfade, dizi öğeleri için yeni başlatma değerleri sağlayamaz.  
  
- **Sırası.** `ReDim`İfade, dizinin derecesini (boyut sayısı) değiştiremiyor.  
  
- **Preserve ile yeniden boyutlandırma.** Kullanırsanız `Preserve` , yalnızca dizinin son boyutunu yeniden boyutlandırabilirsiniz. Diğer tüm boyutlar için, var olan dizinin bir ilişkisini belirtmeniz gerekir.  
  
     Örneğin, dizide yalnızca bir boyut varsa, en son ve yalnızca boyutu değiştirdiğiniz için bu boyutu yeniden boyutlandırabilir ve dizinin tüm içeriğini koruyabilirsiniz. Ancak, dizide iki veya daha fazla boyut varsa, kullanırsanız yalnızca son boyutun boyutunu değiştirebilirsiniz `Preserve` .  
  
- **Özelliklerinin.** `ReDim`Bir değer dizisini tutan bir özelliği kullanabilirsiniz.  
  
## <a name="behavior"></a>Davranış  
  
- **Dizi değiştirme.** `ReDim` Mevcut diziyi serbest bırakır ve aynı dereceye sahip yeni bir dizi oluşturur. Yeni dizi, dizi değişkeninde yayınlanan dizinin yerini alır.  
  
- **Preserve olmadan başlatma.** Belirtmezseniz `Preserve` , `ReDim` Yeni dizinin öğelerini, veri türleri için varsayılan değeri kullanarak başlatır.  
  
- **Preserve ile başlatma.** Belirtirseniz `Preserve` , Visual Basic öğeleri varolan diziden yeni diziye kopyalar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, dizideki mevcut verileri kaybetmeden dinamik bir dizinin en son boyutunun boyutunu artırır ve sonra boyutu kısmi veri kaybıyla azaltır. Son olarak, boyutu özgün değerine geri düşürür ve tüm dizi öğelerini yeniden başlatır.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 `Dim`İfade üç boyutlu yeni bir dizi oluşturur. Her boyut 10 ' un bir bağı ile bildirildiği için her boyutun dizi dizini 0 ile 10 arasında değişebilir. Aşağıdaki tartışmada, üç boyut katman, satır ve sütun olarak adlandırılır.  
  
 İlki, `ReDim` değişkende var olan dizinin yerini alan yeni bir dizi oluşturur `intArray` . `ReDim` Varolan dizideki tüm öğeleri yeni diziye kopyalar. Ayrıca, her katmandaki her satırın sonuna 10 daha fazla sütun ekler ve bu yeni sütunlardaki öğeleri 0 ' a ( `Integer` dizinin öğe türü olan varsayılan değeri) başlatır.  
  
 İkincisi `ReDim` başka bir yeni dizi oluşturur ve uygun olan tüm öğeleri kopyalar. Ancak, her katmandaki her satırın sonundan beş sütun kaybolur. Bu sütunları kullanmayı bitirdiğinizde bu bir sorun değildir. Büyük bir dizinin boyutunu azaltmak artık ihtiyaç duymayacak belleği serbest bırakabilirsiniz.  
  
 Üçüncü, `ReDim` Yeni bir dizi oluşturur ve her katmandaki her satırın sonundan başka beş sütunu kaldırır. Bu kez, var olan herhangi bir öğeyi kopyalamaz. Bu ifade, diziyi özgün boyutuna geri döndürür. İfadeyi `Preserve` değiştirici içermediğinden, tüm dizi öğelerini özgün varsayılan değerlerine ayarlar.  
  
 Daha fazla örnek için bkz. [diziler](../../programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IndexOutOfRangeException>
- [Const Deyimi](const-statement.md)
- [Dim Deyimi](dim-statement.md)
- [Erase Deyimi](erase-statement.md)
- [Yapma](../nothing.md)
- [Diziler](../../programming-guide/language-features/arrays/index.md)
