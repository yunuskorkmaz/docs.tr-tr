---
title: 'Sorun giderme: metin dosyalarından okuma ve yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333793"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Sorun giderme: metin dosyalarından okuma ve yazma (Visual Basic)

Bu konu, metin dosyalarıyla çalışırken karşılaşılan sık karşılaşılan sorunları tartışır ve her birine bir yaklaşım önerir.  
  
## <a name="common-problems"></a>Sık karşılaşılan sorunlar  

 Metin dosyalarıyla çalışırken karşılaşılan en sık karşılaşılan sorunlar arasında güvenlik özel durumları, dosya kodlamaları veya geçersiz yollar yer almaktadır.  
  
### <a name="security-exceptions"></a>Güvenlik özel durumları  

 Bir <xref:System.Security.SecurityException> güvenlik hatası oluştuğunda A atılır. Bu genellikle, kullanıcının gerekli izinlerden yoksun olmasının bir sonucudur ve bu izinler eklenerek veya yalıtılmış depolama daki dosyalarla çalışarak çözülebilir.  
  
### <a name="file-encodings"></a>Dosya kodlamaları  

 Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işlenirken karakterlerin nasıl temsil edilecek lerini belirtir. Metin dosyasındaki beklenmeyen karakterler yanlış kodlamadan kaynaklanabilir. Çoğu dosya için, unicode genellikle tercih edilse de, bir kodlama hangi dil karakterlerini işleyebileceği veya işleyemeyeceği açısından diğerine göre tercih edilebilir. Daha fazla bilgi için Dosya <xref:System.Text.Encoding> [Kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) ve .  
  
### <a name="incorrect-paths"></a>Yanlış yollar  

 Dosya yollarını, özellikle de göreli yolları ayrıştırırken, yanlış verileri sağlamak kolaydır. Doğru yolu sağladığından emin olunarak birçok sorun düzeltilebilir. Daha fazla bilgi için [bkz: Dosya Yollarını Ayrışdırın.](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
