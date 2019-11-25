---
title: Seri Hale Getirme Bağlayıcısı Kullanımı
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138653"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="72f60-102">Seri Hale Getirme Bağlayıcısı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="72f60-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="72f60-103">Bu örnek, serileştirildiğinde genel bir türün sürümünü değiştirmek için <xref:System.Runtime.Serialization.SerializationBinder> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="72f60-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="72f60-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="72f60-104">Demonstrates</span></span>  
 <span data-ttu-id="72f60-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="72f60-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="72f60-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="72f60-106">Discussion</span></span>  
 <span data-ttu-id="72f60-107">Bu örnek, .NET Framework farklı sürümlerini hedefleyen iki varlığın ikili biçimlendirici ve serileştirme cildi kullanarak nasıl iletişim kurabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72f60-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="72f60-108">Bu örnek .NET uzaktan Iletişim kullanılarak geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="72f60-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="72f60-109">Bu, genel türler içeren bir sözleşme uygulayan .NET Framework 4 ve iki farklı istemci, bir hedef .NET Framework 2,0 ve başka bir hedefleme .NET Framework 4 ' ü hedefleyen bir sunucudan oluşur.</span><span class="sxs-lookup"><span data-stu-id="72f60-109">It consists of a server targeting .NET Framework 4, which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting .NET Framework 4.</span></span>  
  
 <span data-ttu-id="72f60-110">Sunucu, tür sürümlerini serileştirme olarak değiştirmek için ikili biçimlendirici bir <xref:System.Runtime.Serialization.SerializationBinder> iliştirir, böylece her iki istemci da bu türlerin düzgün şekilde seri durumdan çıkarabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72f60-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="72f60-111">Bunu ayarlamak için örneği oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="72f60-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="72f60-112">İstemcisini yürütmek için, SBGenericsVTS (6 proje) çözümüne sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="72f60-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="72f60-113">**Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve **birden çok başlangıç**projesi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="72f60-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="72f60-114">Önce **sunucu** ' yı, ardından **Client20** ve ardından **Client40**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="72f60-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="72f60-115">Bu üç proje için **Başlat** eylemini seçin ve REST öğesini **none**olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="72f60-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="72f60-116">**Tamam** ' a tıklayın ve ardından örneği çalıştırmak için F5 ' e basın.</span><span class="sxs-lookup"><span data-stu-id="72f60-116">Click **OK** and then press F5 to run the sample.</span></span>
