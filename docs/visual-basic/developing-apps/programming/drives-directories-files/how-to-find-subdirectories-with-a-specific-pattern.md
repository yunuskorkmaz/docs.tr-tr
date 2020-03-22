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

Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunur dizeler koleksiyonunu döndürür. `wildCards` Belirli bir desen belirtmek için parametrekullanabilirsiniz. Alt dizinlerin içeriğini aramaya eklemek isterseniz, parametreyi `searchType` ' `SearchOption.SearchAllSubDirectories`ye göre ayarlayın.

Belirtilen desenle eşleşen dizinler bulunmazsa boş bir koleksiyon döndürülür.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir desene sahip alt dizinleri bulmak için

Aramak `GetDirectories` istediğiniz dizinin adını ve yolunu sağlayarak yöntemi kullanın. Aşağıdaki örnek, dizin yapısında kendi adlarında "Günlükler" sözcüğünü içeren tüm `ListBox1`dizinleri döndürür ve bunları .

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).

- Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).

- Belirtilen joker karakterlerden biri veya `Nothing`birkaçı boş bir dizedir<xref:System.ArgumentNullException>veya yalnızca boşluk içerir ( ).

- `directory`yok (<xref:System.IO.DirectoryNotFoundException>).

- `directory`varolan bir dosyaya işaret eder (<xref:System.IO.IOException>).

- Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).

- Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).

- Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).

- Kullanıcı gerekli izinleri yoksun<xref:System.UnauthorizedAccessException>( ).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
