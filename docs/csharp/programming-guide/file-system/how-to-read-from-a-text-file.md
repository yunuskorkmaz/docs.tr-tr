---
title: Metin dosyasından okuma - C# Programlama Kılavuzu
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705021"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Metin dosyasından okuma (C# Programlama Kılavuzu)
Bu örnek, statik yöntemleri <xref:System.IO.File.ReadAllText%2A> kullanarak ve <xref:System.IO.File.ReadAllLines%2A> sınıftan bir <xref:System.IO.File?displayProperty=nameWithType> metin dosyasının içeriğini okur.  
  
Kullanan bir örnek <xref:System.IO.StreamReader>için, [metin dosyasını bir defada bir satırda nasıl okunabildiğini](./how-to-read-a-text-file-one-line-at-a-time.md)görün.
  
> [!NOTE]
> Bu örnekte kullanılan dosyalar bir metin [dosyasına nasıl yazılır](./how-to-write-to-a-text-file.md)konusunda oluşturulur.
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu kopyalayın ve C# konsol uygulamasına yapıştırın.  
  
Metin dosyalarını [metin dosyasına yazma hakkında niçin](./how-to-write-to-a-text-file.md)kullanmıyorsanız, `ReadAllText` bağımsız `ReadAllLines` değişkeni bilgisayarınızdaki uygun yol ve dosya adı ile değiştirin.
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya belirtilen konumda yok veya yok. Dosya adının yolunu ve yazımını denetleyin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosyanın içeriğini belirlemek için bir dosyanın adına güvenmeyin. Örneğin, dosya `myFile.cs` C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
