---
title: "Seri Hale Getirme Bağlayıcısı Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e35df7934ffb330feb45e5ff7167c9715f2d291e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="a5883-102">Seri Hale Getirme Bağlayıcısı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a5883-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="a5883-103">Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Runtime.Serialization.SerializationBinder> , serileştirildiğinde genel bir tür sürümünü değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="a5883-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a5883-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="a5883-104">Demonstrates</span></span>  
 <span data-ttu-id="a5883-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="a5883-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a5883-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="a5883-106">Discussion</span></span>  
 <span data-ttu-id="a5883-107">Bu örnek, farklı sürümlerini hedefleyen nasıl iki varlık göstermektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ikili biçimlendirici ve seri hale getirme Bağlayıcısı kullanılarak iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="a5883-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="a5883-108">Bu örnek geliştirme gerçekleştirildi .NET uzaktan iletişim kullanma.</span><span class="sxs-lookup"><span data-stu-id="a5883-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="a5883-109">Bir sunucu hedefleme, örnek oluşur [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], genel türler ve bir hedefleme iki farklı istemci ile bir sözleşme uygulayan [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] ve başka bir hedefleme [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5883-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="a5883-110">Sunucu ekler bir <xref:System.Runtime.Serialization.SerializationBinder> türleri sürümünü değiştirmek için ikili biçimlendirici için uygun şekilde serileştirme üzerinde böylece her iki istemcinin çıkarabilen bu türlerde düzgün.</span><span class="sxs-lookup"><span data-stu-id="a5883-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a5883-111">Ayarlamak için derleme ve örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a5883-111">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="a5883-112">İstemci yürütmek için SBGenericsVTS çözüme sağ tıklayın (6 projeleri) ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a5883-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a5883-113">İçinde **ortak özellikleri**seçin **başlangıç projesi**seçeneğini belirleyip **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="a5883-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="a5883-114">Seçin **Server** ilk, ardından **Client20** ve ardından **Client40**.</span><span class="sxs-lookup"><span data-stu-id="a5883-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="a5883-115">Seçin **Başlat** bu üç eylem projeleri ve ayarlamak rest bırakın **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="a5883-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4.  <span data-ttu-id="a5883-116">Tıklatın **Tamam** örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a5883-116">Click **OK** and then press F5 to run the sample.</span></span>
