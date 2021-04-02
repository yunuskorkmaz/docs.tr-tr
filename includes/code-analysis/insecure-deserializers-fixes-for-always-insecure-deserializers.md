---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96588731"
---
- <span data-ttu-id="f0926-101">Mümkünse, bunun yerine güvenli bir serileştirici kullanın ve **bir saldırganın seri durumdan çıkarmak için rastgele bir tür belirtmesini sağlayın**.</span><span class="sxs-lookup"><span data-stu-id="f0926-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="f0926-102">Bazı güvenli serileştiriciler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="f0926-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="f0926-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Hiçbir şekilde kullanmayın <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f0926-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f0926-104">Bir tür Çözümleyicisi kullanmanız gerekiyorsa, serisi kaldırılan türleri beklenen bir listeyle kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="f0926-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="f0926-105">Newtonsoft Json.NET-TypeNameHandling. None kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0926-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="f0926-106">TypeNameHandling için başka bir değer kullanmanız gerekiyorsa, serisi kaldırılan türleri özel bir ISerializationBinder ile beklenen bir listeyle kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="f0926-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="f0926-107">Protokol Arabellekleri</span><span class="sxs-lookup"><span data-stu-id="f0926-107">Protocol Buffers</span></span>

- <span data-ttu-id="f0926-108">Seri hale getirilen verileri prova yapın.</span><span class="sxs-lookup"><span data-stu-id="f0926-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="f0926-109">Serileştirmeden sonra, serileştirilmiş verileri şifreli olarak imzalayın.</span><span class="sxs-lookup"><span data-stu-id="f0926-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="f0926-110">Seri durumdan önce, şifreleme imzasını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f0926-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="f0926-111">Şifreleme anahtarını, önemli döndürmeler için açıklanmasını ve tasarıma karşı koruyun.</span><span class="sxs-lookup"><span data-stu-id="f0926-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
