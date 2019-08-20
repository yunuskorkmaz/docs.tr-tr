---
title: 'Nasıl yapılır: Metin dosyasından okuma- C# Programlama Kılavuzu'
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
ms.openlocfilehash: c424f7884dd7242152bda1b16943f6489194299f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589990"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Nasıl yapılır: Metin dosyasından okuma (C# Programlama Kılavuzu)
Bu örnek, statik yöntemleri <xref:System.IO.File.ReadAllText%2A> ve <xref:System.IO.File.ReadAllLines%2A> <xref:System.IO.File?displayProperty=nameWithType> sınıfından kullanarak bir metin dosyasının içeriğini okur.  
  
 Tarafından kullanılan <xref:System.IO.StreamReader>bir örnek için bkz [. nasıl yapılır: Bir metin dosyasını tek seferde bir satır okur](./how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Bu örnekte [kullanılan dosyalar, konusunda nasıl yapılır: Bir metin dosyasına](./how-to-write-to-a-text-file.md)yazın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu kopyalayın ve bir C# konsol uygulamasına yapıştırın.  
  
 Metin dosyalarını [şu şekilde kullanarak kullanmıyorsanız: Bir metin dosyasına](./how-to-write-to-a-text-file.md)yazın, `ReadAllText` bağımsız değişkenini `ReadAllLines` bilgisayarınızdaki uygun yol ve dosya adıyla değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Dosya yok veya belirtilen konumda yok. Dosya adının yolunu ve yazımını denetleyin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Dosyanın içeriğini belirlemekte bir dosyanın adına güvenmeyin. Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
