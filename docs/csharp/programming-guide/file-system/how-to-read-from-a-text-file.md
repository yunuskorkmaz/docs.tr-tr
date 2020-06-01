---
title: Bir metin dosyasından okuma-C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 8f79d22a86390ca931b05262e50865d852c154c7
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241753"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Bir metin dosyasından okuma (C# Programlama Kılavuzu)
Bu örnek, statik yöntemleri ve sınıfından kullanarak bir metin dosyasının içeriğini okur <xref:System.IO.File.ReadAllText%2A> <xref:System.IO.File.ReadAllLines%2A> <xref:System.IO.File?displayProperty=nameWithType> .  
  
Kullanan bir örnek için <xref:System.IO.StreamReader> , bkz. [bir metin dosyasını tek seferde bir satır okuma](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Bu örnekte kullanılan dosyalar, [bir metin dosyasına nasıl yazılacağı](./how-to-write-to-a-text-file.md)konusunda oluşturulur.
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.  
  
[Bir metin dosyasına yazma](./how-to-write-to-a-text-file.md)işleminden gelen metin dosyalarını kullanmıyorsanız, bağımsız değişkenini `ReadAllText` `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya yok veya belirtilen konumda yok. Dosya adının yolunu ve yazımını denetleyin.  
  
## <a name="net-security"></a>.NET güvenliği  
 Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin. Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
