---
title: 'Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 047d566c13f03803d2e5c3bc6cce0db56df4a3f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345844"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)
Bir yordamın [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi varsa, parametre dizisi için tek boyutlu bir dizi alan aşırı yüklenmiş bir sürüm tanımlayamazsınız. Daha fazla bilgi için, [yordamları aşırı yükleme konusunda dikkat edilmesi gereken](./considerations-in-overloading-procedures.md)"ParamArray parametresi Için örtük aşırı yüklemeler" konusuna bakın.  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Değişken sayıda parametre alan bir yordamı aşırı yüklemek için  
  
1. Bu yordamın ve kod mantığının aşırı yüklenmiş sürümlerden `ParamArray` bir parametreden daha fazla avantaj sağladığı yokunular. "Aşırı yüklemeler ve ParamArrays" konusuna bakın ve daha fazla [yordamda göz](./considerations-in-overloading-procedures.md)atın.  
  
2. Yordamın parametre listesinin değişken bölümünde kabul etmesi gereken değer sayısını belirleme. Bu durum, hiçbir değer olmaması durumunda olabilir ve tek boyutlu bir dizinin durumunu içerebilir.  
  
3. Her kabul edilebilir sayıda sağlanan değer için, karşılık gelen parametre listesini tanımlayan bir `Sub` veya `Function` bildirim bildirimi yazın. Bu aşırı yüklenmiş sürümde `Optional` ya da `ParamArray` anahtar sözcüğünü kullanmayın.  
  
4. Her bildirimde, `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin.  
  
5. Her bildirime göre, çağıran kod bu bildirimin parametre listesine karşılık gelen değerleri sağladığı zaman yürütülmesi gereken yordam kodunu yazın.  
  
6. Her yordamı uygun şekilde `End Sub` veya `End Function` ifadesiyle sonlandırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresiyle tanımlanan bir yordamı ve daha sonra eşdeğer bir yordam kümesini gösterir.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Parametre dizisi için tek boyutlu bir dizi alan bir parametre listesiyle bu tür bir yordamı aşırı yükleyemezsiniz. Ancak, diğer örtük aşırı yüklemelerin imzalarını kullanabilirsiniz. Aşağıdaki bildirimlerde bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Aşırı yüklenmiş sürümlerindeki kodun, çağıran kodun `ParamArray` parametresi için bir veya daha fazla değer sağlayıp sağlamamasını veya bu durumda kaç tane olacağını test etmek zorunda değildir. Visual Basic, denetimi çağıran bağımsız değişken listesiyle eşleşen sürüme geçirir.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 `ParamArray` parametresine sahip bir yordam aşırı yüklenmiş sürümlerin bir kümesiyle eşdeğer olduğundan, böyle bir yordamı bu örtük aşırı yüklemelerin herhangi birine karşılık gelen bir parametre listesiyle birlikte yükleyemezsiniz. Daha fazla bilgi için bkz. [yordamları aşırı yükleme konuları](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır. Bir parametre dizisini kabul ediyorsanız, kendisine geçilen çağıran kodun dizinin uzunluğunu test etmeli ve uygulamanız için çok büyükse uygun adımları uygulamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
