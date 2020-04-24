---
title: 'Nasıl Yapılır: Metin Dosyalarından Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334587"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Metin Dosyalarını Okuma

`My.Computer.FileSystem` Nesnesinin <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> yöntemi bir metin dosyasından okumanızı sağlar. Dosyanın içeriği ASCII veya UTF-8 gibi bir kodlama kullanıyorsa dosya kodlaması belirtilebilir.

Genişletilmiş karakterler içeren bir dosyadan okuma yapıyorsanız, dosya kodlamasını belirtmeniz gerekir.

> [!NOTE]
> Tek seferde tek satırlık bir dosyayı okumak için <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> `My.Computer.FileSystem` nesnenin yöntemini kullanın. `OpenTextFileReader` metodu bir <xref:System.IO.StreamReader> nesnesi döndürür. Tek seferde bir dosyayı <xref:System.IO.StreamReader.ReadLine%2A> bir satırı okumak `StreamReader` için nesnesinin yöntemini kullanabilirsiniz. `StreamReader` Nesnesinin <xref:System.IO.StreamReader.EndOfStream%2A> yöntemini kullanarak dosyanın sonuna kadar test edebilirsiniz.

## <a name="to-read-from-a-text-file"></a>Bir metin dosyasından okumak için

Bir metin `ReadAllText` dosyasının içeriğini bir `My.Computer.FileSystem` dizeye okumak ve yolu sağlamak için nesnesinin yöntemini kullanın. Aşağıdaki örnek, test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Kodlanmış bir metin dosyasından okumak için

Bir metin `ReadAllText` dosyasının içeriğini bir `My.Computer.FileSystem` dizeye okumak için nesnesinin yöntemini kullanın, yol ve dosya kodlama türünü sağlar. Aşağıdaki örnek, UTF32 biçimindeki test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (<xref:System.ArgumentException>).

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.

- Dosya yok (<xref:System.IO.FileNotFoundException>).

- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu (<xref:System.IO.IOException>).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Dizeyi arabelleğe (<xref:System.OutOfMemoryException>) yazmak için yeterli bellek yok.

- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.

Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.

Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarını Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Nasıl Yapılır: Sabit Genişlikli Metin Dosyalarını Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Dosya Kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
