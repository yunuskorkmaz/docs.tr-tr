---
title: 'Sorun giderme: Okuma ve yazma metin dosyaları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 90a04d9de2ac77c28a92d99e1fe118a1f8ecf448
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831793"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Sorun giderme: Okuma ve yazma metin dosyaları (Visual Basic)
Bu konuda metinle çalışma dosyaları ve her bir yaklaşım önerir sık karşılaşılan sorunlar ele alınmıştır.  
  
## <a name="common-problems"></a>Yaygın sorunlar  
 Metin dosyaları ile çalışma karşılaşılan en yaygın sorunları, güvenlik özel durumları, Dosya kodlamaları veya geçersiz yollarını içerir.  
  
### <a name="security-exceptions"></a>Güvenlik özel durumları  
 A <xref:System.Security.SecurityException> bir güvenlik hatası oluştuğunda oluşturulur. Bu genellikle kullanıcının eksik izinler ekleyerek veya yalıtılmış depolamadaki dosyaları ile çalışma çözülmesi gerekli izinler sonucudur.  
  
### <a name="file-encodings"></a>Dosya kodlamaları  
 Dosya kodlamaları olarak da bilinen karakter kodlamalarını temsil etmek nasıl belirtin ne zaman karakter metin işleme. Bir metin dosyasında beklenmeyen karakter hatalı kodlama neden olabilir. Unicode genellikle tercih edilir olsa da çoğu dosya için bir kodlama başka hangi dil karakterlerini açısından olabilir veya işleyemez, tercih edilebilir. Daha fazla bilgi için [Dosya kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) ve <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Yanlış yol  
 Dosya yollarını ayrıştırma, özellikle göreli yolları da yanlış veri sağlamak kolay. Doğru yolu sağladığınız sağlayarak karşılaşılan birçok sorun düzeltilebilir. Daha fazla bilgi için [nasıl yapılır: Dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Dosyalara Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
