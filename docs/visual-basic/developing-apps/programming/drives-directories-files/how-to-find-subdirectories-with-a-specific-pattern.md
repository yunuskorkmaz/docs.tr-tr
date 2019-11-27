---
title: 'Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348768"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> yöntemi, bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. Belirli bir kalıbı belirtmek için `wildCards` parametresini kullanabilirsiniz. Aramaya alt dizinlerin içeriğini eklemek istiyorsanız, `searchType` parametresini `SearchOption.SearchAllSubDirectories`olarak ayarlayın.

Belirtilen Düzenle eşleşen hiçbir dizin bulunamazsa boş bir koleksiyon döndürülür.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir düzene sahip alt dizinleri bulmak için

Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak `GetDirectories` yöntemini kullanın. Aşağıdaki örnek, dizin yapısındaki, adında "Logs" sözcüğünü içeren tüm dizinleri döndürür ve bunları `ListBox1`ekler.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.

- Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.

- Belirtilen bir veya daha fazla joker karakter `Nothing`, boş bir dize veya yalnızca boşluk içeriyor (<xref:System.ArgumentNullException>).

- `directory` yok (<xref:System.IO.DirectoryNotFoundException>).

- `directory` var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).

- Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).

- Kullanıcının gerekli izinleri yok (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
