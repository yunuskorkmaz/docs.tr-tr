---
title: 'Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348768"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma

Yöntemi <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> , bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. Belirli bir kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz. Aramada alt dizinlerin içeriğini eklemek istiyorsanız, `searchType` parametresini olarak `SearchOption.SearchAllSubDirectories`ayarlayın.

Belirtilen Düzenle eşleşen hiçbir dizin bulunamazsa boş bir koleksiyon döndürülür.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir düzene sahip alt dizinleri bulmak için

Arama yapmak `GetDirectories` istediğiniz dizinin adını ve yolunu sağlayarak yöntemini kullanın. Aşağıdaki örnek, dizin yapısındaki, adında "Logs" sözcüğünü içeren tüm dizinleri döndürür ve içine ekler `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.

- Belirtilen Joker karakterlerden biri veya birkaçı `Nothing`, boş bir dize veya yalnızca boşluk (<xref:System.ArgumentNullException>) içeriyor.

- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).

- `directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.

- Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
