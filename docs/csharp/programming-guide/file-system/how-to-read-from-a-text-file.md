---
title: Metin dosyasından okuma- C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705021"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Bir metin dosyasından okuma (C# Programlama Kılavuzu)
Bu örnek, <xref:System.IO.File?displayProperty=nameWithType> sınıfından statik yöntemleri <xref:System.IO.File.ReadAllText%2A> ve <xref:System.IO.File.ReadAllLines%2A> kullanarak bir metin dosyasının içeriğini okur.  
  
<xref:System.IO.StreamReader>kullanan bir örnek için, bkz. bir [metin dosyasını tek seferde bir satır okuma](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Bu örnekte kullanılan dosyalar, [bir metin dosyasına nasıl yazılacağı](./how-to-write-to-a-text-file.md)konusunda oluşturulur.
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.  
  
[Bir metin dosyasına yazma](./how-to-write-to-a-text-file.md)işleminden gelen metin dosyalarını kullanmıyorsanız, bağımsız değişkeni `ReadAllText` ve `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya yok veya belirtilen konumda yok. Dosya adının yolunu ve yazımını denetleyin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin. Örneğin, `myFile.cs` dosyası bir C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
