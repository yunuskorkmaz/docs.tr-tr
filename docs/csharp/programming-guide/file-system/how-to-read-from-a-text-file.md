---
title: 'Nasıl Yapılır: Bir metin dosyasından - okuma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 67e98750af589a3deb5e9d0d51f8b1204fdaad84
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240313"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Nasıl Yapılır: Bir metin dosyasından okuma (C# Programlama Kılavuzu)
Bu örnek statik yöntemleri kullanarak bir metin dosyasının içeriğini okur <xref:System.IO.File.ReadAllText%2A> ve <xref:System.IO.File.ReadAllLines%2A> gelen <xref:System.IO.File?displayProperty=nameWithType> sınıfı.  
  
 Kullanan bir örnek için <xref:System.IO.StreamReader>, bkz: [nasıl yapılır: Bir metin dosyası bir satırı okumak](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Bu örnekte kullanılan dosyaları konusunda oluşturulan [nasıl yapılır: Bir metin dosyasına yazma](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu kopyalayın ve C# konsol uygulamasına yapıştırın.  
  
 Metin dosyalarından kullanmıyorsanız [nasıl yapılır: Bir metin dosyasına yazma](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), bağımsız değişkeni Değiştir `ReadAllText` ve `ReadAllLines` bilgisayarınızda uygun yolu ve dosya adı ile.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Dosya yok veya belirtilen konumda yok. Yol ve dosya adının yazımını denetleyin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosyanın içeriğini belirlemek için bir dosya adına güvenmeyin. Örneğin, dosyayı `myFile.cs` bir C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.IO?displayProperty=nameWithType>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
