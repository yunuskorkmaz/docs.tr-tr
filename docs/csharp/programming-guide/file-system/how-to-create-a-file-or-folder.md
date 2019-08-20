---
title: 'Nasıl yapılır: Dosya veya klasör oluşturma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: c29d0638e2429119020fee5317d40a95b00e40ef
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590109"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Nasıl yapılır: Dosya veya klasör oluşturma (C# Programlama Kılavuzu)
Bilgisayarınızda program aracılığıyla bir klasör oluşturabilir, bir alt klasör oluşturabilir, alt klasörde bir dosya oluşturabilir ve verileri dosyaya yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey yapmaz ve hiçbir özel durum oluşturulmaz. Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> varolan bir dosyayı yeni bir dosya ile değiştirir. Örnek, varolan bir `if` dosyanın değiştirilmesini engellemek için bir - `else` ifade kullanır.  
  
 Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosyanın zaten mevcut olup olmadığına bağlı olarak farklı sonuçlar belirtebilirsiniz. Böyle bir dosya yoksa, kod bir tane oluşturur. Böyle bir dosya varsa, kod bu dosyaya veri ekler.  
  
- Rastgele olmayan bir dosya adı belirtin.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- İfadesini aşağıdaki koddaki ifadesiyledeğiştirin.`using` `if` - `else`  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Her seferinde verilerin dosyaya eklendiğini doğrulamak için örneği birkaç kez çalıştırın.  
  
 Deneyebileceğiniz daha `FileMode` fazla değer için bkz <xref:System.IO.FileMode>.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Klasör adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıf) içeriyor. Geçerli yol adları oluşturmak için sınıfınıkullanın.<xref:System.IO.Path>  
  
- Oluşturulacak klasörün üst klasörü salt okunurdur (<xref:System.IO.IOException> sınıf).  
  
- Klasör adı `null` (<xref:System.ArgumentNullException> sınıf).  
  
- Klasör adı çok uzun (<xref:System.IO.PathTooLongException> sınıf).  
  
- Klasör adı yalnızca bir iki nokta üst üste, ":"<xref:System.IO.PathTooLongException> (sınıf).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kısmi güven durumlarında <xref:System.Security.SecurityException> sınıfın bir örneği oluşturulabilir.  
  
 Klasörü oluşturma izniniz yoksa, örnek <xref:System.UnauthorizedAccessException> sınıfının bir örneğini oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
