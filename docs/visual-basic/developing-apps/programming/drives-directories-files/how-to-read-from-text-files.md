---
title: 'Nasıl yapılır: Metin Dosyalarını Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 0d99209ed123686355e8d49c82ba23f94084f895
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411622"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Metin Dosyalarını Okuma

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> `My.Computer.FileSystem` Nesnesinin yöntemi bir metin dosyasından okumanızı sağlar. Dosyanın içeriği ASCII veya UTF-8 gibi bir kodlama kullanıyorsa dosya kodlaması belirtilebilir.

Genişletilmiş karakterler içeren bir dosyadan okuma yapıyorsanız, dosya kodlamasını belirtmeniz gerekir.

> [!NOTE]
> Tek seferde tek satırlık bir dosyayı okumak için <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> nesnenin yöntemini kullanın `My.Computer.FileSystem` . `OpenTextFileReader` metodu bir <xref:System.IO.StreamReader> nesnesi döndürür. Tek seferde bir <xref:System.IO.StreamReader.ReadLine%2A> `StreamReader` dosyayı bir satırı okumak için nesnesinin yöntemini kullanabilirsiniz. Nesnesinin yöntemini kullanarak dosyanın sonuna kadar test edebilirsiniz <xref:System.IO.StreamReader.EndOfStream%2A> `StreamReader` .

## <a name="to-read-from-a-text-file"></a>Bir metin dosyasından okumak için

`ReadAllText` `My.Computer.FileSystem` Bir metin dosyasının içeriğini bir dizeye okumak ve yolu sağlamak için nesnesinin yöntemini kullanın. Aşağıdaki örnek, test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Kodlanmış bir metin dosyasından okumak için

`ReadAllText` `My.Computer.FileSystem` Bir metin dosyasının içeriğini bir dizeye okumak için nesnesinin yöntemini kullanın, yol ve dosya kodlama türünü sağlar. Aşağıdaki örnek, UTF32 biçimindeki test.txt dosyasının içeriği okuyup bir dize haline getirir ve sonra da bir ileti kutusunda görüntüler.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu ( <xref:System.ArgumentException> ).

- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .

- Dosya yok ( <xref:System.IO.FileNotFoundException> ).

- Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.

- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).

- Dizeyi arabelleğe () yazmak için yeterli bellek yok <xref:System.OutOfMemoryException> .

- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .

Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.

Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Dosyalardan Okuma](reading-from-files.md)
- [Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](how-to-read-from-comma-delimited-text-files.md)
- [Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma](how-to-read-from-fixed-width-text-files.md)
- [Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](how-to-read-from-text-files-with-multiple-formats.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](troubleshooting-reading-from-and-writing-to-text-files.md)
- [İzlenecek Yol: Visual Basic'te Dosyaları ve Dizinleri Düzenleme](walkthrough-manipulating-files-and-directories.md)
- [Dosya Kodlamaları](file-encodings.md)
