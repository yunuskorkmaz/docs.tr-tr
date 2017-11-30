---
title: "Nasıl yapılır: Bir Metin Dosyasına Yazma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Nasıl yapılır: Bir Metin Dosyasına Yazma (C# Programlama Kılavuzu)
Bu örnekler bir metin dosyasına yazmanın çeşitli yollarını göstermektedir.  İlk iki örnek statik kullanışlı yöntemler kullanın <xref:System.IO.File?displayProperty=nameWithType> herhangi IEnumerable her öğeye yazmak için sınıf\<dize > ve bir metin dosyasına bir dize.  Örnek 3 veya dosyaya yazmak gibi her satır ayrı ayrı işlemek varsa bir dosyaya metin eklemek nasıl gösterir.  Örnek 1-3 dosyasındaki tüm var olan içeriğin üzerine ancak örnek 4 varolan bir dosyaya metin ekleneceği gösterilmiştir.  
  
 Tüm bu örneklerde dize değişmez değerleri dosyalara yazmasını ancak büyük olasılıkla kullanmak istersiniz <xref:System.String.Format%2A> ile veya olmadan doldurma ve benzeri bir alanda farklı türlerdeki değerleri sağa veya sola hizalı yazmak için birçok denetimleri olan yöntemi.  Ayrıca C# kullanabilirsiniz [dize ilişkilendirme](../../../csharp/language-reference/keywords/interpolated-strings.md) özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Tüm bu örneklerde dize değişmez değerleri dosyalara yazmasını ancak büyük olasılıkla kullanmak istersiniz <xref:System.String.Format%2A> ile veya olmadan doldurma ve benzeri bir alanda farklı türlerdeki değerleri sağa veya sola hizalı yazmak için birçok denetimleri olan yöntemi.  Ayrıca C# kullanabilirsiniz [dize ilişkilendirme](../../../csharp/language-reference/keywords/interpolated-strings.md) özelliği.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dosya mevcut ve salt okunur.  
  
-   Yol adı çok uzun olabilir.  
  
-   Disk dolu olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)  
 [Örnek: bir koleksiyon uygulama depoya kaydedin.](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
