---
title: 'Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401634"
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

- `directory`yok ( <xref:System.IO.DirectoryNotFoundException> ).

- `directory`var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .

- Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.

- Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).

- Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .

- Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Nasıl yapılır: Belirli bir Düzendeki Dosyaları Bulma](how-to-find-files-with-a-specific-pattern.md)
