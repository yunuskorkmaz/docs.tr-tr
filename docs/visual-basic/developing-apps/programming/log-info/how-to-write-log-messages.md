---
title: 'Nasıl yapılır: Günlük iletileri (Visual Basic) yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: c12d0cde7d8128400769cd2e93361bb10e08f59b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967028"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Nasıl yapılır: Günlük iletileri (Visual Basic) yazma
Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızla ilgili bilgileri günlüğe kaydetmek için nesneleri. Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` izleme bilgileri günlüğe kaydetmek için yöntemi.  
  
 Özel durum bilgilerini günlük için kullanma `My.Application.Log.WriteException` yöntemi; bkz: [nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntemi.  
  
 [!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Günlüğe yazma veri kullanıcı parolalar gibi hassas bilgiler içermediğinden emin olun. Daha fazla bilgi için [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı yeri değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
