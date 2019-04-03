---
title: 'Nasıl yapılır: Bir belirsiz sayıda parametre (Visual Basic) isteyen bir yordamı aşırı yükleme'
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
ms.openlocfilehash: bae420e88a74fbe3f7e8ad3592133fdcaf191029
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839005"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Nasıl yapılır: Bir belirsiz sayıda parametre (Visual Basic) isteyen bir yordamı aşırı yükleme
Bir yordam varsa bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi, parametre dizisi için tek boyutlu bir dizi alan aşırı yüklenmiş bir sürümünü tanımlayamaz. Daha fazla bilgi için bkz: "Örtük aşırı yüklemeleri için bir ParamArray parametresiyle" [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Değişken sayıda parametre isteyen bir yordamı aşırı yükleme için  
  
1.  Yordam ve kod mantıksal avantajlarından çağırma sürümlerinden birden fazla aşırı anlamamıza bir `ParamArray` parametresi. "Aşırı yüklemeler ve ParamArrays" konularına bakın [yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md).  
  
2.  Sağlanan değerler hangi sayıda yordam parametre listesi değişken parçası kabul etmelidir belirleyin. Bu değer harf içerebilir ve tek tek boyutlu bir dizi harf içerebilir.  
  
3.  Sağlanan değerler kabul edilebilir her sayısı için yazma bir `Sub` veya `Function` bildirim deyimindeki, karşılık gelen parametre listesi tanımlar. Ya da kullanmayın `Optional` veya `ParamArray` anahtar sözcüğü Bu aşırı yüklenmiş bir sürüm.  
  
4.  Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğü ile [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.  
  
5.  Her bildirimi çağıran kod, bildirimin parametre listesine karşılık gelen değerlerini sağlayan, yürütülecek yordamı kod yazın.  
  
6.  Her bir yordam sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tanımlı bir yordam gösterir. bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi ve aşırı yüklenmiş yordamları eşdeğer bir dizi.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Böyle bir yordam bir parametre listesiyle parametre dizisi için tek boyutlu bir dizi alan aşırı yükleyemez. Ancak, bir örtük aşırı imzalarını kullanabilirsiniz. Aşağıdaki bildirimleri bu göstermektedir.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Çağıran kod tarafından sağlanan bir veya daha fazla değer için olup olmadığını sınamak aşırı yüklenmiş sürümleri kodda yok `ParamArray` parametresi veya ise, kaç tane. Visual Basic denetim çağırma bağımsız değişken listesiyle eşleşen sürüme geçer.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Çünkü bir yordama bir `ParamArray` parametre kümesi aşırı yüklü sürümler için eşdeğerdir, örtük Bu aşırı yüklemeler birine karşılık gelen bir parametre listesi ile bu tür bir yordamı aşırı yüklenemez. Daha fazla bilgi için [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Süresiz olarak büyük olabilecek bir dizi işlem olduğunda, uygulamanızın bazı iç kapasite taşmasını riski yoktur. Bir parametre dizisi kabul ederseniz, çağıran kodun geçirilen dizinin uzunluğunu test etmek ve uygulamanız için çok büyük ise, uygulamanız gereken adımlar gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
