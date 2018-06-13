---
title: 'Nasıl yapılır: Dosya ve Klasör Oluşturma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: d69885b420d28878072a70dfd2288905cf13de1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334840"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Nasıl yapılır: Dosya ve Klasör Oluşturma (C# Programlama Kılavuzu)
Programlı olarak bilgisayarınızda bir klasör oluşturun, bir alt klasör oluşturun alt klasöründe bir dosya oluşturun ve veri dosyasına yazma.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 Bu klasör zaten mevcutsa <xref:System.IO.Directory.CreateDirectory%2A> yoksa hiçbir şey ve hiçbir özel durum oluşur. Ancak, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> varolan bir dosyanın yeni bir dosya ile değiştirir. Örnek kullanan bir `if` - `else` değiştirilmekte olan varolan bir dosyanın önlemek için deyimi.  
  
 Örnekte aşağıdaki değişiklikler yaparak, belirli bir ada sahip bir dosya zaten var olup üzerinde göre farklı sonuçlar belirtebilirsiniz. Böyle bir dosya yoksa, bir kod oluşturur. Böyle bir dosya varsa, kodu bu dosyaya veri ekler.  
  
-   Rasgele olmayan bir dosya adı belirtin.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   Değiştir `if` - `else` deyimiyle `using` deyimi aşağıdaki kodda.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Birkaç kez örneği çalıştırmak bu verileri doğrulamak için dosyayı her zaman eklenir.  
  
 Daha fazla bilgi için `FileMode` , bakın, deneyebilirsiniz değerleri <xref:System.IO.FileMode>.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Klasör adı yanlış biçimlendirilmiş. Örneğin, geçersiz karakterler içeriyor veya yalnızca boşluk (<xref:System.ArgumentException> sınıfı). Kullanım <xref:System.IO.Path> geçerli bir yol adları oluşturmasını sağlar.  
  
-   Oluşturulacak klasörünün üst klasörü salt okunurdur (<xref:System.IO.IOException> sınıfı).  
  
-   Klasör adı `null` (<xref:System.ArgumentNullException> sınıfı).  
  
-   Klasör adı çok uzun (<xref:System.IO.PathTooLongException> sınıfı).  
  
-   Yalnızca bir iki nokta üst üste, bir klasör adı olduğundan ":" (<xref:System.IO.PathTooLongException> sınıfı).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Örneği <xref:System.Security.SecurityException> sınıfı kısmi güven durumlarda oluşturulur.  
  
 Klasörü oluşturmak için izne sahip değilseniz, örnek örneği oluşturur <xref:System.UnauthorizedAccessException> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
