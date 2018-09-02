---
title: 'Nasıl yapılır: EdmGen.exe Model ve eşleme dosyalarını doğrulama için kullanın'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: fda8698381e98c64318f1a26f77f0263e9085074
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43471932"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>Nasıl yapılır: EdmGen.exe Model ve eşleme dosyalarını doğrulama için kullanın
Bu konu nasıl kullanılacağını gösterir [EDM Oluşturucu (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) model ve eşleme dosyalarını doğrulama aracı. Daha fazla bilgi için [varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>Okul modeli EdmGen.exe kullanarak doğrulamak için  
  
1.  School veritabanını oluşturun. Daha fazla bilgi için [School örnek veritabanını oluşturma](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Okul modeli oluşturur. Daha fazla bilgi için [nasıl yapılır: kullanımı Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: el ile bir Entity Framework projesinin yapılandırma](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET varlık veri modeli araçları](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Nasıl yapılır: sorgu performansını artırmak için görünümleri önceden oluştur](https://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
