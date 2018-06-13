---
title: Visual Basic'de Genel Yordamlar
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 686087e4520ea5e6e69e5906c628af3ad54749da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649402"
---
# <a name="generic-procedures-in-visual-basic"></a>Visual Basic'de Genel Yordamlar
A *genel yordam*, olarak da bilinir bir *genel yöntem*, bir yordamı ile en az bir tür parametresi tanımlı değil. Bu yordam çağrıları her saat veri türleri için kendi gereksinimlerine uyarlamak çağıran kodu sağlar.  
  
 Bir yordam yalnızca genel bir sınıf veya genel yapısı içinde tanımlanan genel değil. Genel olması için yordam bunun sürebilir normal parametreleri yanı sıra en az bir tür parametre almalıdır. Genel sınıf veya yapı nongeneric yordamları ve nongeneric bir sınıf, yapı, içerebilir veya modülü genel yordamlar içerebilir.  
  
 Genel bir yordam, normal parametre listesinde bir ve kendi yordamdaki kodu varsa, dönüş türü türü parametrelerini kullanabilirsiniz.  
  
## <a name="type-inference"></a>Tür Çıkarma  
 Herhangi bir tür bağımsız değişkeni girmeden genel yordam çağırabilirsiniz. Bu şekilde çağırmak için yordam tür bağımsız değişkeni geçirmek için uygun veri türlerini belirlemek derleyici çalışır. Bu adlı *türü çıkarımı*. Aşağıdaki kod bir çağrı gösterir derleyici türü geçirmelisiniz oluşturur, `String` tür parametresi için `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Tür bağımsız değişkenleri aramanız bağlamından derleyici gösterilemez bir hata bildirir. Böyle bir hata bir olası nedeni bir dizi derece eşleşmemesidir. Örneğin, bir tür parametresi bir dizi normal parametresini tanımlama varsayalım. Genel yordam çağrısı, farklı bir derece (boyutları sayısı), bir dizi sağladığını uyuşmazlığı tür çıkarımı başarısız olmasına neden olur. Aşağıdaki kod bir çağrı gösterir, iki boyutlu bir dizi tek boyutlu dizi bekliyor yordamına geçirilen içinde.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Tür çıkarımı yalnızca tüm tür bağımsız değişkenleri kaldırarak çağırabilirsiniz. Bir tür bağımsız değişkeni sağlarsanız, tümünü sağlamanız gerekir.  
  
 Tür çıkarımı yalnızca genel yordamlar için desteklenir. Tür çıkarımı Genel sınıflar, yapılar, arabirimleri veya temsilciler üzerinde çağrılamıyor.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, genel tanımlar `Function` bir dizide belirli bir öğeyi bulmak için yordamı. Bir tür parametresi tanımlar ve parametre listesinde iki parametre oluşturmak için kullanılır.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Açıklamalar  
 Önceki örnekte karşılaştırmak olanağı gerektirir `searchValue` her öğeye karşı `searchArray`. Bu yeteneği sağlamak amacıyla, tür parametresi kısıtlar `T` uygulamak için <xref:System.IComparable%601> arabirimi. Kod kullanan <xref:System.IComparable%601.CompareTo%2A> yöntemi yerine `=` işleci, tür bağımsız değişkeni için sağlanan garanti olduğundan `T` destekler `=` işleci.  
  
 Test edebilirsiniz `findElement` aşağıdaki kodla yordamı.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Yukarıdaki çağrılar `MsgBox` sırasıyla görüntü "0", "1" ve "-1".  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Yordamlar](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Tür Listesi](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Parametre Listesi](../../../../visual-basic/language-reference/statements/parameter-list.md)
