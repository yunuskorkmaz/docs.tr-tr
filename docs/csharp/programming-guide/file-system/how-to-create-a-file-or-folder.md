---
title: 'Nasıl yapılır: Bir dosya veya klasör - oluşturma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: d94c3624b84b2fea6760ac8f36fc592928a55834
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680746"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Nasıl yapılır: Bir dosya veya klasör oluşturma (C# Programlama Kılavuzu)
Programlı olarak bilgisayarınızda bir klasör oluşturun, bir alt klasör oluşturun alt klasöründe bir dosya oluşturun ve dosyaya veri yazmak.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Klasör zaten varsa, <xref:System.IO.Directory.CreateDirectory%2A> hiçbir şey ve hiçbir özel durum atılmaz. Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> mevcut bir dosyayı yeni bir dosya ile değiştirir. Örnekte bir `if` - `else` varolan bir dosyanın değiştirilmesini önlemek için deyimi.  
  
 Örnekte aşağıdaki değişiklikleri yaparak, belirli bir ada sahip bir dosya zaten var olup üzerinde göre farklı sonuçlar belirtebilirsiniz. Böyle bir dosya yoksa, kod bir tane oluşturur. Böyle bir dosya varsa, kod verileri bu dosyaya ekler.  
  
- Rastgele olmayan dosya adı belirtin.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Değiştirin `if` - `else` deyimiyle `using` aşağıdaki kodda deyimi.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Örneği birkaç kere çalıştırın verileri doğrulamak için dosyayı her seferinde eklenir.  
  
 Daha fazla bilgi için `FileMode` , bkz, deneyebileceğiniz değerleri <xref:System.IO.FileMode>.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Klasör adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı). Kullanım <xref:System.IO.Path> geçerli yol adları oluşturmak için sınıf.  
  
- Oluşturulacak klasörün üst klasörü salt okunurdur (<xref:System.IO.IOException> sınıfı).  
  
- Klasör adı `null` (<xref:System.ArgumentNullException> sınıfı).  
  
- Klasör adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).  
  
- Yalnızca bir iki nokta üst üste, klasör adı olan ":" (<xref:System.IO.PathTooLongException> sınıfı).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Örneği <xref:System.Security.SecurityException> sınıfı kısmi güven durumlarda oluşturulur.  
  
 Klasör oluşturma izniniz yoksa, örnek bir örneğini atar <xref:System.UnauthorizedAccessException> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
