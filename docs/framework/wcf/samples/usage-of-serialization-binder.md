---
title: Seri Hale Getirme Bağlayıcısı Kullanımı
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 47a1974386927316ea9230ec27cf647d7245c44a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007597"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="dd473-102">Seri Hale Getirme Bağlayıcısı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dd473-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="dd473-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Runtime.Serialization.SerializationBinder> , serileştirilmiş olduğunda, genel bir türün sürümü değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="dd473-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="dd473-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="dd473-104">Demonstrates</span></span>  
 <span data-ttu-id="dd473-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="dd473-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="dd473-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="dd473-106">Discussion</span></span>  
 <span data-ttu-id="dd473-107">Bu örnek, farklı sürümlerini hedefleme nasıl iki varlık gösterir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ikili biçimlendirici serileştirme Bağlayıcısı ile iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="dd473-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="dd473-108">Bu örnek geliştirilmesini bitti .NET uzaktan iletişim kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dd473-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="dd473-109">Bir sunucu hedefleme örneği oluşur [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], genel türler ve iki farklı istemcilerin hedefleyen bir sözleşme uygulayan [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] ve başka bir hedefleme [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd473-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="dd473-110">Sunucu ekler bir <xref:System.Runtime.Serialization.SerializationBinder> türleri sürümünü değiştirmek için ikili biçimlendirici için uygun şekilde seri hale getirme üzerinde bu nedenle her iki istemcinin seri durumdan çıkarabilen türlerine düzgün.</span><span class="sxs-lookup"><span data-stu-id="dd473-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dd473-111">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dd473-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="dd473-112">İstemci yürütmek için SBGenericsVTS çözüme sağ tıklayın (6 projeler) ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dd473-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="dd473-113">İçinde **ortak özellikler**seçin **başlangıç projesi**, ardından **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="dd473-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="dd473-114">Seçin **sunucu** ilk, ardından **Client20** ardından **Client40**.</span><span class="sxs-lookup"><span data-stu-id="dd473-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="dd473-115">Seçin **Başlat** bu üç eylem projeleri ve ayarlamak geri kalan bırakın **hiçbiri**.</span><span class="sxs-lookup"><span data-stu-id="dd473-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="dd473-116">Tıklayın **Tamam** ve örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dd473-116">Click **OK** and then press F5 to run the sample.</span></span>
