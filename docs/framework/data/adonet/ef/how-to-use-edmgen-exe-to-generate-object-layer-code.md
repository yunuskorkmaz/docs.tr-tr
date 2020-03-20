---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1dbd2e25d5f9795af4f80e079c6a0b807666743d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150564"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma
Bu konu, .csdl dosyasını temel alan nesne katmanı kodu oluşturmak için [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) aracının nasıl kullanılacağını gösterir.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe kullanarak Visual Basic projesi için Okul modeli için nesne katmanı kodu oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))  
  
2. Okul modelini oluşturun veya School.csdl dosyasını edinin. Daha fazla bilgi için [bkz: Modeli oluşturmak ve Dosyaları Eşleme için EdmGen.exe'yi kullanın.](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
3. Komut isteminde, satır sonları olmadan aşağıdaki komutu uygulayın:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen.exe kullanarak c# projesi için Okul modeli için nesne katmanı kodu oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))  
  
2. Okul modelini oluşturun veya School.csdl dosyasını edinin. Daha fazla bilgi için [bkz: Modeli oluşturmak ve Dosyaları Eşleme için EdmGen.exe'yi kullanın.](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
3. Komut isteminde, satır sonları olmadan aşağıdaki komutu uygulayın:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Modelleme ve Eşleme](modeling-and-mapping.md)
- [Nasıl?](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Varlık Veri Modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapilir: Sorgu Performansını Artırmak için Görünümleri Önceden Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
