---
title: Metin dosyasına yazma- C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712253"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Metin dosyasına yazma (C# Programlama Kılavuzu)
Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir. İlk iki örnek, her bir `IEnumerable<string>` ve bir dizenin her bir öğesini bir metin dosyasına yazmak için <xref:System.IO.File?displayProperty=nameWithType> sınıfında statik kolay yöntemler kullanır. Örnek 3 ' te, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceği gösterilmektedir. Örnekler 1-3 dosyadaki tüm varolan içeriğin üzerine yazılır, ancak örnek 4 ' te varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.  
  
 Bu örneklerin tümü dosyalara dize değişmez değerleri yazar. Dosyaya yazılan metni biçimlendirmek istiyorsanız <xref:System.String.Format%2A> yöntemi veya C# [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliğini kullanın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya mevcut ve salt okunur.  
  
- Yol adı çok uzun olabilir.  
  
- Disk dolu olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
- [Örnek: bir koleksiyonu uygulama depolamasına kaydetme](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
