---
title: Bir dosya veya klasör oluşturma-C# Programlama Kılavuzu
description: Program aracılığıyla bir dosya veya klasör oluşturmayı öğrenin. Bir klasör, alt klasör, alt klasörde bir dosya oluşturabilir ve bu dosyaya veri yazabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: f5641dc765b1a2d62adb76babe3f111730d4550b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302691"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Dosya veya klasör oluşturma (C# Programlama Kılavuzu)
Bilgisayarınızda program aracılığıyla bir klasör oluşturabilir, bir alt klasör oluşturabilir, alt klasörde bir dosya oluşturabilir ve verileri dosyaya yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey yapmaz ve hiçbir özel durum oluşturulmaz. Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> varolan bir dosyayı yeni bir dosya ile değiştirir. Örnek, varolan bir `if` - `else` dosyanın değiştirilmesini engellemek için bir ifade kullanır.  
  
 Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosyanın zaten mevcut olup olmadığına bağlı olarak farklı sonuçlar belirtebilirsiniz. Böyle bir dosya yoksa, kod bir tane oluşturur. Böyle bir dosya varsa, kod bu dosyaya veri ekler.  
  
- Rastgele olmayan bir dosya adı belirtin.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- `if` - `else` İfadesini `using` aşağıdaki koddaki ifadesiyle değiştirin.  
  
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
  
 Deneyebileceğiniz daha fazla `FileMode` değer için bkz <xref:System.IO.FileMode> ..  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Klasör adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk ( <xref:System.ArgumentException> sınıf) içeriyor. <xref:System.IO.Path>Geçerli yol adları oluşturmak için sınıfını kullanın.  
  
- Oluşturulacak klasörün üst klasörü salt okunurdur ( <xref:System.IO.IOException> sınıf).  
  
- Klasör adı `null` ( <xref:System.ArgumentNullException> sınıf).  
  
- Klasör adı çok uzun ( <xref:System.IO.PathTooLongException> sınıf).  
  
- Klasör adı yalnızca bir iki nokta üst üste, ":" ( <xref:System.IO.PathTooLongException> sınıf).  
  
## <a name="net-security"></a>.NET güvenliği  
 <xref:System.Security.SecurityException>Kısmi güven durumlarında sınıfın bir örneği oluşturulabilir.  
  
 Klasörü oluşturma izniniz yoksa, örnek sınıfının bir örneğini oluşturur <xref:System.UnauthorizedAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
