---
title: 'Nasıl yapılır: Metin dosyasına yazma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: d08fe23f2dbfe46c0a58084b05610dfe7db3dda9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589924"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Nasıl yapılır: Metin dosyasına yazma (C# Programlama Kılavuzu)
Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir. İlk iki örnek, bir metin dosyasına bir <xref:System.IO.File?displayProperty=nameWithType> `IEnumerable<string>` ve dizesinin her bir öğesini yazmak için sınıfında statik kolay yöntemler kullanır. Örnek 3 ' te, dosyaya yazarken her satırı ayrı olarak işlemek gerektiğinde bir dosyaya nasıl metin ekleneceği gösterilmektedir. Örnekler 1-3 dosyadaki tüm varolan içeriğin üzerine yazılır, ancak örnek 4 ' te varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.  
  
 Bu örneklerin tümü dosyalara dize değişmez değerleri yazar. Dosyaya yazılmış metni biçimlendirmek isterseniz, <xref:System.String.Format%2A> yöntemi veya [](../../language-reference/tokens/interpolated.md) C# dize ilişkilendirme özelliğini kullanın.  
  
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
- [Örnekli Bir koleksiyonu uygulama depolamasına kaydetme](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
