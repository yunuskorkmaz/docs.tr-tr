---
title: Metin dosyasına yazma-C# Programlama Kılavuzu
description: C# ile bir metin dosyası yazmayı öğrenin. Çeşitli kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 02/11/2021
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.topic: how-to
ms.custom: contperf-fy21q3
ms.openlocfilehash: ecc3ba73161d4f4571bbc6ae0c9aaa3337586ef7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475623"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Metin dosyasına yazma (C# Programlama Kılavuzu)

Bu makalede, bir dosyaya metin yazmanın çeşitli yollarını gösteren birkaç örnek vardır. İlk iki örnek, <xref:System.IO.File?displayProperty=nameWithType> herhangi bir öğesinin her `IEnumerable<string>` bir öğesini bir metin dosyasına yazmak için sınıfında statik kolay yöntemler kullanır `string` . Üçüncü örnek, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceğini gösterir. İlk üç örnekte, dosyadaki tüm varolan içeriğin üzerine yazarsınız. Son örnek, varolan bir dosyaya nasıl metin ekleneceğini gösterir.

 Bu örneklerin tümü dosyalara dize değişmez değerleri yazar. Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya C# [String enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanın.

## <a name="write-a-collection-of-strings-to-a-file"></a>Bir dosyaya dizeler koleksiyonu yazma

:::code language="csharp" source="snippets/write-text/WriteAllLines.cs":::

Yukarıdaki kaynak kodu örneği:

- Üç değerli bir dize dizisi oluşturur.
- Abuna bir çağrıyı bekler <xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> :

  - Zaman uyumsuz bir dosya adı *WriteLines.txt* oluşturur. Dosya zaten varsa, üzerine yazılır.
  - Verilen satırları dosyaya yazar.
  - Dosyayı kapatır, gerektiğinde otomatik olarak reçeteye ve elden atılıyor.

## <a name="write-one-string-to-a-file"></a>Bir dosyaya bir dize yaz

:::code language="csharp" source="snippets/write-text/WriteAllText.cs":::

Yukarıdaki kaynak kodu örneği:

- Atanan dize sabit değeri verilen bir dizeyi başlatır.
- Abuna bir çağrıyı bekler <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> :

  - Zaman uyumsuz bir dosya adı *WriteText.txt* oluşturur. Dosya zaten varsa, üzerine yazılır.
  - Verilen metni dosyaya yazar.
  - Dosyayı kapatır, gerektiğinde otomatik olarak reçeteye ve elden atılıyor.

## <a name="write-selected-strings-from-an-array-to-a-file"></a>Seçili dizeleri bir diziden bir dosyaya yaz

:::code language="csharp" source="snippets/write-text/StreamWriterOne.cs":::

Yukarıdaki kaynak kodu örneği:

- Üç değerli bir dize dizisi oluşturur.
- Bir <xref:System.IO.StreamWriter> *WriteLines2.txt* dosya yolu ile bir [using bildirimi](../../whats-new/csharp-8.md#using-declarations)olarak başlatır.
- Tüm satırlarda yinelenir.
- Koşullu olarak öğesine bir çağrı bekler <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> , bu, satır içermiyorsa dosyayı dosyaya yazar `"Second"` .

## <a name="append-text-to-an-existing-file"></a>Varolan bir dosyaya metin ekle

:::code language="csharp" source="snippets/write-text/StreamWriterTwo.cs":::

Yukarıdaki kaynak kodu örneği:

- Üç değerli bir dize dizisi oluşturur.
- Bir <xref:System.IO.StreamWriter> *WriteLines2.txt* dosya yolu ile, bir [using bildirimi](../../whats-new/csharp-8.md#using-declarations)olarak bir örneğini başlatır ve `true` sonuna ekleyin.
- ' A bir çağrısını bekler <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType> , bu, dizeyi dosyaya eklenen bir satır olarak yazar.

## <a name="exceptions"></a>Özel durumlar

Aşağıdaki koşullar özel bir duruma neden olabilir:

- <xref:System.InvalidOperationException>: Dosya var ve salt okunurdur.
- <xref:System.IO.PathTooLongException>: Yol adı çok uzun olabilir.
- <xref:System.IO.IOException>: Disk dolu olabilir.

Dosya sistemi ile çalışırken özel durumlara neden olabilecek ek koşullar vardır. Bu, en iyi şekilde programlama savunmalarıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
- [Örnek: bir koleksiyonu uygulama depolamasına kaydetme](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
