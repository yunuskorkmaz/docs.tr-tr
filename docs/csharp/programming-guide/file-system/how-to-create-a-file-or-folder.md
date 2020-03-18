---
title: Dosya veya klasör oluşturma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167563"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Dosya veya klasör oluşturma (C# Programlama Kılavuzu)
Bilgisayarınızda programlı bir klasör oluşturabilir, bir alt klasör oluşturabilir, alt klasörde bir dosya oluşturabilir ve dosyaya veri yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey yapmaz ve hiçbir özel durum atılır. Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> varolan bir dosyayı yeni bir dosyayla değiştirir. Örnek, varolan bir dosyanın değiştirilmesini önlemek için bir `if` - `else` deyim kullanır.  
  
 Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosyanın zaten var olup olmadığına bağlı olarak farklı sonuçlar belirtebilirsiniz. Böyle bir dosya yoksa, kod bir dosya oluşturur. Böyle bir dosya varsa, kod verileri o dosyaya ekler.  
  
- Rasgele olmayan bir dosya adı belirtin.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- İfadeyi `if` - `else` aşağıdaki `using` koddaki deyimle değiştirin.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Verilerin her seferinde dosyaya eklenmesini doğrulamak için örneği birkaç kez çalıştırın.  
  
 Deneyebileceğiniz `FileMode` daha fazla değer <xref:System.IO.FileMode>için bkz.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Klasör adı yanlış biçimlendirilmiş. Örneğin, yasadışı karakterler içerir veya yalnızca beyaz<xref:System.ArgumentException> boşluk (sınıf) olduğunu. Geçerli <xref:System.IO.Path> yol adları oluşturmak için sınıfı kullanın.  
  
- Oluşturulacak klasörün üst klasörü salt okunur<xref:System.IO.IOException> (sınıf) olur.  
  
- Klasör adı `null` (sınıf).<xref:System.ArgumentNullException>  
  
- Klasör adı çok uzun<xref:System.IO.PathTooLongException> (sınıf).  
  
- Klasör adı sadece bir iki<xref:System.IO.PathTooLongException> nokta üst üste, ":" (sınıf).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.Security.SecurityException> Sınıfın bir örneği kısmi güven durumlarında atılabilir.  
  
 Klasörü oluşturma izniniz yoksa, örnek sınıfın bir örneğini <xref:System.UnauthorizedAccessException> atar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
