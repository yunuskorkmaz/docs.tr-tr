---
description: 'Hakkında daha fazla bilgi için: nasıl yapılır: Visual Basic Ikili dosyalardan okuma'
title: 'Nasıl yapılır: İkili Dosyalardan Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 0d522c6f55c0ef2e39437ba732040afdf5113d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797516"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te İkili Dosyaları Okuma

`My.Computer.FileSystem`Nesnesi, `ReadAllBytes` ikili dosyalardan okumak için yöntemini sağlar.  
  
### <a name="to-read-from-a-binary-file"></a>İkili dosyadan okumak için  
  
- `ReadAllBytes`Bir dosyanın içeriğini bayt dizisi olarak döndüren yöntemini kullanın. Bu örnek dosyadan okur `C:/Documents and Settings/selfportrait.jpg` .  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- Büyük ikili dosyalar için, <xref:System.IO.FileStream.Read%2A> <xref:System.IO.FileStream> tek seferde yalnızca belirtilen bir miktarı dosyadan okumak için nesnesinin yöntemini kullanabilirsiniz. Böylece, her okuma işlemi için dosyanın belleğe ne kadarının yüklendiğini sınırlayabilirsiniz. Aşağıdaki kod örneği bir dosyayı kopyalar ve çağıranın okuma işlemi başına ne kadar dosyanın belleğe okunduğunu belirtmesini sağlar.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:  
  
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

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Dosyalardan Okuma](reading-from-files.md)
- [Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma](how-to-read-from-text-files-with-multiple-formats.md)
- [Verileri Panoda Depolama ve Panodan Okuma](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
