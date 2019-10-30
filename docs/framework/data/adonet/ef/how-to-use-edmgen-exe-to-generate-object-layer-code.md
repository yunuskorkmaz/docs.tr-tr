---
title: 'Nasıl yapılır: EdmGen. exe kullanarak nesne katmanı kodu oluşturma'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 9182f815a502488f955f64f6c19aad7865d0c7c6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039978"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a>Nasıl yapılır: EdmGen. exe kullanarak nesne katmanı kodu oluşturma
Bu konu,. csdl dosyasını temel alan nesne katmanı kodu oluşturmak için [EDM Oluşturucu (EdmGen. exe)](edm-generator-edmgen-exe.md) aracının nasıl kullanılacağını gösterir.  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen. exe kullanarak bir Visual Basic projesi için okul modeline yönelik nesne katmanı kodu oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Okul modelini oluşturun veya okul. csdl dosyasını edinin. Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyaları oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen. exe kullanarak bir C# projenin okul modeline yönelik nesne katmanı kodu oluşturmak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Okul modelini oluşturun veya okul. csdl dosyasını edinin. Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyaları oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Modelleme ve Eşleme](modeling-and-mapping.md)
- [Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
