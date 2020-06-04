---
title: 'Nasıl yapılır: Günlük İletileri Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410055"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)

`My.Application.Log` `My.Log` Uygulamanız hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini günlüğe kaydetmek için yönteminin nasıl kullanılacağını gösterir.

Özel durum bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteException` yöntemini kullanın; bkz. [nasıl yapılır: günlük özel durumları](how-to-log-exceptions.md).

## <a name="example"></a>Örnek

Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntemini kullanır.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Günlüğe yazdığınız verilerin kullanıcı parolaları gibi hassas bilgileri içermediğinden emin olun. Daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](how-to-log-exceptions.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Çıktısını Filtreleme](walkthrough-filtering-my-application-log-output.md)
