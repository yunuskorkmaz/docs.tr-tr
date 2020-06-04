---
title: 'Nasıl yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 7e263e2c9035db54dbb58c6c78c0647d5442504e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401712"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli Düzendeki Dosyaları Dizine Kopyalama

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. `wildCards`Belirli bir kalıbı belirtmek için parametresini kullanabilirsiniz.  
  
 Eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>Dosyaları bir dizine kopyalamak için yöntemini kullanabilirsiniz.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Belirli bir düzene sahip dosyaları dizine kopyalamak için  
  
1. `GetFiles`Dosya listesini döndürmek için yöntemini kullanın. Bu örnek, belirtilen dizindeki tüm. rtf dosyalarını döndürür.  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. `CopyFile`Dosyaları kopyalamak için yöntemini kullanın. Bu örnek, dosyalarını adlı dizine kopyalar `testdirectory` .  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. İfadesini `For` bir `Next` ifadesiyle kapatın.  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, yukarıdaki kod parçacıklarını tüm biçimde gösterir, belirtilen dizindeki tüm. rtf dosyalarını adlı dizine kopyalar `testdirectory` .  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .  
  
- Dizin yok ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- Dizin, var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .  
  
- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.  
  
- Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).  
  
- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> . Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma](how-to-find-subdirectories-with-a-specific-pattern.md)
- [Sorun Giderme: Metin Dosyalarını Okuma ve Yazma](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma](how-to-get-the-collection-of-files-in-a-directory.md)
