---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic belirli bir düzene sahip alt dizinleri bulma'
title: 'Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: aaf1fe0e844c6a3db2b011289613a80dbd1b43fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797555"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>Yöntemi, bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür. `wildCards`Belirli bir kalıbı belirtmek için parametresini kullanabilirsiniz. Aramada alt dizinlerin içeriğini eklemek istiyorsanız, `searchType` parametresini olarak ayarlayın `SearchOption.SearchAllSubDirectories` .

Belirtilen Düzenle eşleşen hiçbir dizin bulunamazsa boş bir koleksiyon döndürülür.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Belirli bir düzene sahip alt dizinleri bulmak için

`GetDirectories`Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak yöntemini kullanın. Aşağıdaki örnek, dizin yapısındaki, adında "Logs" sözcüğünü içeren tüm dizinleri döndürür ve içine ekler `ListBox1` .

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Güçlü Programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).

- Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .

- Belirtilen Joker karakterlerden biri veya birkaçı `Nothing` , boş bir dize veya yalnızca boşluk ( <xref:System.ArgumentNullException> ) içeriyor.

- `directory` yok ( <xref:System.IO.DirectoryNotFoundException> ).

- `directory` var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).

- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .

- Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl yapılır: Belirli bir Düzendeki Dosyaları Bulma](how-to-find-files-with-a-specific-pattern.md)
