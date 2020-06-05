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
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387887"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)
Bir yordamın [ParamArray](../../../language-reference/modifiers/paramarray.md) parametresi varsa, parametre dizisi için tek boyutlu bir dizi alan aşırı yüklenmiş bir sürüm tanımlayamazsınız. Daha fazla bilgi için, [yordamları aşırı yükleme konusunda dikkat edilmesi gereken](./considerations-in-overloading-procedures.md)"ParamArray parametresi Için örtük aşırı yüklemeler" konusuna bakın.  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Değişken sayıda parametre alan bir yordamı aşırı yüklemek için  
  
1. Yordamın ve kod mantığının, aşırı yüklenmiş sürümlerden daha fazla bir parametreden daha fazla avantaj sağladığı yokunular `ParamArray` . "Aşırı yüklemeler ve ParamArrays" konusuna bakın ve daha fazla [yordamda göz](./considerations-in-overloading-procedures.md)atın.  
  
2. Yordamın parametre listesinin değişken bölümünde kabul etmesi gereken değer sayısını belirleme. Bu durum, hiçbir değer olmaması durumunda olabilir ve tek boyutlu bir dizinin durumunu içerebilir.  
  
3. Her kabul edilebilir sayıda sağlanan değer için, `Sub` `Function` karşılık gelen parametre listesini tanımlayan bir veya bildirim bildirimi yazın. `Optional` `ParamArray` Bu aşırı yüklenmiş sürümde ya da anahtar sözcüğünü kullanmayın.  
  
4. Her bildirimde, `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin.  
  
5. Her bildirime göre, çağıran kod bu bildirimin parametre listesine karşılık gelen değerleri sağladığı zaman yürütülmesi gereken yordam kodunu yazın.  
  
6. Her yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir [ParamArray](../../../language-reference/modifiers/paramarray.md) parametresiyle tanımlanan bir yordamı ve daha sonra eşdeğer bir yordam kümesini gösterir.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Parametre dizisi için tek boyutlu bir dizi alan bir parametre listesiyle bu tür bir yordamı aşırı yükleyemezsiniz. Ancak, diğer örtük aşırı yüklemelerin imzalarını kullanabilirsiniz. Aşağıdaki bildirimlerde bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Aşırı yüklenmiş sürümlerindeki kodun, çağıran kodun parametre için bir veya daha fazla değer sağlayıp sağlamamasını ya da bu durumda kaç tane olacağını test etmek zorunda değildir `ParamArray` . Visual Basic, denetimi çağıran bağımsız değişken listesiyle eşleşen sürüme geçirir.  
  
## <a name="compile-the-code"></a>Kodu derle  
 Parametresine sahip bir yordam `ParamArray` aşırı yüklenmiş sürümlerin bir kümesiyle eşdeğer olduğundan, bu tür bir yordamı, bu örtük aşırı yüklemelerin herhangi birine karşılık gelen bir parametre listesiyle birlikte yükleyemezsiniz. Daha fazla bilgi için bkz. [yordamları aşırı yükleme konuları](./considerations-in-overloading-procedures.md).  
  
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
- [Aşırı yükleme çözümlemesi](./overload-resolution.md)
