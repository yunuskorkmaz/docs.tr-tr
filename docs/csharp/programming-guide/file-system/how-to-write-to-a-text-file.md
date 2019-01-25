---
title: 'Nasıl yapılır: -Bir metin dosyasına yazma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ce0321d91835fbdf6c37f4b7736f0de900e9f838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666806"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Nasıl yapılır: Bir metin dosyasına yazma (C# Programlama Kılavuzu)
Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir. İlk iki örnek statik yöntemler kullanın <xref:System.IO.File?displayProperty=nameWithType> her öğe herhangi yazmak için sınıf `IEnumerable<string>` ve bir metin dosyasına bir dize. Örnek 3, dosyaya yazmak gibi her satır ayrı ayrı işlemeniz gerektiğinde bir dosyaya metin ekleme gösterir. Örnek 1-3 dosyasındaki tüm varolan içeriğin üzerine, ancak örnek 4 varolan bir dosyaya nasıl metin ekleneceği gösterilmektedir.  
  
 Bu örneklerin tümü dosyalara dize değişmez değerleri yazmaktadır. Bir dosyaya yazılacak Metin biçimlendirmek istediğiniz kullanırsanız <xref:System.String.Format%2A> yöntemi veya C# [dize ilişkilendirme](../../../csharp/language-reference/tokens/interpolated.md) özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dosya mevcut ve salt okunur.  
  
-   Yol adı çok uzun olabilir.  
  
-   Disk dolu olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
- [Örnek: Bir koleksiyonu uygulama depolamaya kaydetme](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
