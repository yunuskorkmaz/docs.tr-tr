---
title: Metin dosyasına yazma-C# Programlama Kılavuzu
description: C# ile bir metin dosyası yazmayı öğrenin. Çeşitli kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 4108163121d56268b810121ca3ae2b2c1338aeab
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301651"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Metin dosyasına yazma (C# Programlama Kılavuzu)
Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir. İlk iki örnek, bir <xref:System.IO.File?displayProperty=nameWithType> metin dosyasına bir ve dizesinin her bir öğesini yazmak için sınıfında statik kolay yöntemler kullanır `IEnumerable<string>` . Örnek 3 ' te, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceği gösterilmektedir. Örnekler 1-3 dosyadaki tüm varolan içeriğin üzerine yazılır, ancak örnek 4 ' te varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.  
  
 Bu örneklerin tümü dosyalara dize değişmez değerleri yazar. Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya C# [String enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya mevcut ve salt okunur.  
  
- Yol adı çok uzun olabilir.  
  
- Disk dolu olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
- [Örnek: bir koleksiyonu uygulama depolamasına kaydetme](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
