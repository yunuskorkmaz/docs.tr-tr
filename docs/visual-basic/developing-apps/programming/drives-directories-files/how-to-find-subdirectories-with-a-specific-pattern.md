---
title: 'Nasıl yapılır: Visual Basic belirli bir düzene sahip alt dizinleri bul'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 96ae5c5c44263a47343058012d8b8aa064d9cd92
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039435"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Nasıl yapılır: Visual Basic belirli bir düzene sahip alt dizinleri bul

Yöntemi <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> , bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. Belirli bir kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz. Aramada alt dizinlerin içeriğini eklemek istiyorsanız, `searchType` parametresini olarak `SearchOption.SearchAllSubDirectories`ayarlayın.

Belirtilen Düzenle eşleşen hiçbir dizin bulunamazsa boş bir koleksiyon döndürülür.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir düzene sahip alt dizinleri bulmak için

Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak yönteminikullanın.`GetDirectories` Aşağıdaki örnek, dizin yapısındaki, adında "Logs" sözcüğünü içeren tüm dizinleri döndürür ve içine ekler `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.

- Belirtilen Joker karakterlerden `Nothing`biri veya birkaçı, boş bir dize veya yalnızca boşluk (<xref:System.ArgumentNullException>) içeriyor.

- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).

- `directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.

- Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl yapılır: Belirli bir düzene sahip dosyaları bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
