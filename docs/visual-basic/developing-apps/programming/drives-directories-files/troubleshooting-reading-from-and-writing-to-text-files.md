---
title: "Sorun giderme: Okuma ve yazma metin dosyalarına (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e836f79cd05dbaa180cc7bf5413ce57004e3500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Sorun giderme: Okuma ve yazma metin dosyalarına (Visual Basic)
Bu konuda metinle çalışma dosyaları ve her bir yaklaşım öneren sık karşılaşılan sorunlar ele alınmıştır.  
  
## <a name="common-problems"></a>Sık karşılaşılan sorunları  
 Metin dosyaları ile çalışırken karşılaşılan en yaygın sorunları güvenlik özel durumları, Dosya kodlamaları veya geçersiz yolları içerir.  
  
### <a name="security-exceptions"></a>Güvenlik özel durumları  
 A <xref:System.Security.SecurityException> bir güvenlik hatası oluştuğunda oluşturulur. Bu genellikle bir izinler ekleyerek veya yalıtılmış depolamadaki dosyaları ile çalışma çözülmesi gerekli izinleri yetersiz kullanıcı sonucudur.  
  
### <a name="file-encodings"></a>Dosya kodlamaları  
 Dosya kodlamaları, olarak da bilinen karakter kodlamaları temsil etmek nasıl belirtin ne zaman karakter metin işleme. Bir metin dosyasında beklenmeyen karakter yanlış kodlamadan neden olabilir. Unicode genellikle tercih edilen olmasına rağmen çoğu dosya için bir kodlama başka hangi dil karakterlerini bakımından veya yükleyebilir işleyemez, tercih edilebilir. Daha fazla bilgi için bkz: [Dosya kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) ve <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Yanlış yol  
 Dosya yolları ayrıştırılırken özellikle göreli yollar, yanlış veri sağlamak kolay. Doğru yolu sağladığını sağlayarak birçok sorun düzeltilebilir. Daha fazla bilgi için bkz: [nasıl yapılır: dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [Dosyaları okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Dosyalara yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [TextFieldParser nesnesiyle metin dosyalarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
