---
title: 'Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 62a3bde9d2431b9e9e86e2a8d8896520f3456590
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198125"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama

Bu konuda, bir [EDM Oluşturucu (EdmGen.exe)](edm-generator-edmgen-exe.md) aracının model ve eşleme dosyalarını doğrulamak için nasıl kullanılacağı gösterilmektedir. Daha fazla bilgi için bkz. [varlık veri modeli](../entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>EdmGen.exe kullanarak okul modelini doğrulamak için  
  
1. Okul veritabanını oluşturun. Daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).  
  
2. Okul modelini oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3. Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Entity Framework projesi El Ile yapılandırma](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))
- [ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluşturma](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))
- [Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
