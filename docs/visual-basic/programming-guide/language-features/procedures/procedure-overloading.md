---
title: Yordam Aşırı Yüklemesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 6e8d1fa72c60c4fa3d2237ad24c2d1b4891a7bf2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828244"
---
# <a name="procedure-overloading-visual-basic"></a>Yordam Aşırı Yüklemesi (Visual Basic)
*Aşırı yükleme* bir yordam, birden çok sürümü aynı ada ancak farklı parametre listeleri kullanarak tanımlama anlamına gelir. Aşırı yükleme amacı, ada göre ayırmak zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır. Parametre listesini değiştirerek bunu yapabilirsiniz.  
  
## <a name="overloading-rules"></a>Kuralları aşırı yükleme  
 Bir yordamı aşırı yükleme, aşağıdaki kurallar geçerlidir:  
  
-   **Aynı ada**. Aşırı yüklenen her sürümü aynı yordam adı kullanmanız gerekir.  
  
-   **Farklı imza**. Her Aşırı yüklenen sürümü, diğer aşırı yüklenmiş sürümleri aşağıdaki bakımdan en az birinde farklı olmalıdır:  
  
    -   Parametre sayısı  
  
    -   Parametre sırası  
  
    -   Parametrelerinin veri türleri  
  
    -   Tür parametreleri (için genel bir yordam) sayısı  
  
    -   Dönüş türü (yalnızca bir dönüşüm işleci)  
  
     Yordam adı ile birlikte önceki öğeler toplu olarak adlandırılır *imza* yordamın. Aşırı yüklenmiş bir yordamı çağırdığınızda, derleyici imzayı tanımının çağrı doğru eşleşip eşleşmediğini kontrol için kullanır.  
  
-   **Öğeleri imzasının parçası**. İmza değişen olmadan bir yordamı aşırı yükleyemez. Özellikle, bir veya daha fazla aşağıdaki öğelerin değişen tarafından yalnızca bir yordamı aşırı yüklenemez:  
  
    -   Yordam değiştiricisi anahtar sözcükler gibi `Public`, `Shared`, ve `Static`  
  
    -   Parametresi veya tür parametresi adları  
  
    -   Tür parametresi kısıtlamaları (için genel bir yordam)  
  
    -   Parametre değiştiricisi anahtar sözcükler gibi `ByRef` ve `Optional`  
  
    -   Bir değer olup olmadığını döndürür  
  
    -   (bir dönüşüm işleci dışında) dönüş değerinin veri türü  
  
     Yukarıdaki listede öğeleri imzasının bir parçası değildir. Aşırı yüklü sürümler arasında ayırt etmek için kullanamazsınız olsa da, bunların imzalarını tarafından düzgün bir şekilde ayırt edilen aşırı yüklü sürümler arasında farklılık gösterebilir.  
  
-   **Geç bağlama bağımsız değişkenleri**. Geç bir bağımlı nesne değişkeni aşırı yüklenmiş bir sürüme geçirmek istiyorsanız, uygun bir parametre olarak bildirmeniz gerekir <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Bir yordamın birden fazla sürümünü  
 Yazdığınız varsayalım bir `Sub` müşteriye adı veya hesap numarası başvurabileceğiniz istediğiniz bir müşterinin bakiyesi ve karşı bir işlem göndermeniz için yordamı. Bunu yapabilmek için iki farklı tanımlayabilirsiniz `Sub` yordamlar, aşağıdaki örnekte olduğu gibi:  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a>Aşırı yüklenmiş sürümleri  
 Aşırı yükleme tek yordam adı için bir alternatiftir. Kullanabileceğiniz [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü bir sürümüne ilişkin yordam her parametre listesi için aşağıdaki gibi tanımlayın:  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a>Ek aşırı yüklemeleri  
 Ayrıca herhangi bir işlem tutarı kabul etmek istiyorsanız `Decimal` veya `Single`, daha fazla aşırı `post` Bu çeşitleme için izin vermek için. Siz yaptıysanız her aşırı yüklemeleri önceki örnekte, dört olurdu `Sub` yordamları, aynı ada sahip tüm ancak dört farklı imzalara sahip.  
  
## <a name="advantages-of-overloading"></a>Aşırı yükleme avantajları  
 Bir yordamı aşırı yükleme çağrısının esneklik avantajlarındandır. Kullanılacak `post` yordamı çağıran kod, müşteri kimliği olarak edinebilirsiniz önceki örnekte bildirilen bir `String` veya `Integer`ve ardından her iki durumda da aynı yordamı çağırın. Aşağıdaki örnek bunu göstermektedir:  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
