---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96588731"
---
- Mümkünse, bunun yerine güvenli bir serileştirici kullanın ve **bir saldırganın seri durumdan çıkarmak için rastgele bir tür belirtmesini sağlayın**. Bazı güvenli serileştiriciler şunları içerir:

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Hiçbir şekilde kullanmayın <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> . Bir tür Çözümleyicisi kullanmanız gerekiyorsa, serisi kaldırılan türleri beklenen bir listeyle kısıtlayın.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-TypeNameHandling. None kullanın. TypeNameHandling için başka bir değer kullanmanız gerekiyorsa, serisi kaldırılan türleri özel bir ISerializationBinder ile beklenen bir listeyle kısıtlayın.
  - Protokol Arabellekleri

- Seri hale getirilen verileri prova yapın. Serileştirmeden sonra, serileştirilmiş verileri şifreli olarak imzalayın. Seri durumdan önce, şifreleme imzasını doğrulayın. Şifreleme anahtarını, önemli döndürmeler için açıklanmasını ve tasarıma karşı koruyun.
