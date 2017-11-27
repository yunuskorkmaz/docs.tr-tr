---
title: "Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db4f2ae40d25795b0e5f75ac3612f45834043dfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="c2b1f-102">Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="c2b1f-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="c2b1f-103">Bu konuda, bir kaynak dosyasında kaydedilen saat dilimlerini geri yükleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="c2b1f-104">Bilgi ve saat dilimlerini kaydetme hakkında yönergeler için bkz: [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="c2b1f-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="c2b1f-105">Katıştırılmış bir kaynaktan bir Timezoneınfo nesnesinin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="c2b1f-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="c2b1f-106">Alınacak saat dilimi özel bir saat dilimi değilse, kullanarak örneği çalıştığınızda <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="c2b1f-107">Örneği bir <xref:System.Resources.ResourceManager> tam adını katıştırılmış kaynak dosyasını ve kaynak dosyası içeren bütünleştirilmiş kodun bir başvuru geçirerek nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="c2b1f-108">Katıştırılmış kaynak dosyasının tam adı belirleyemiyorsa, kullanın [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derlemenin bildirimini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="c2b1f-109">Bir `.mresource` giriş kaynağı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="c2b1f-110">Örnekte, kaynağın tam adıdır `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="c2b1f-111">Saat dilimi örneklemesi kodu içeren aynı bütünleştirilmiş kodda katıştırılmış kaynak dosyası varsa, çağırarak ona bir başvuru alabilirsiniz `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="c2b1f-112">Varsa çağrısı <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi başarısız veya özel bir saat dilimi örneğinin oluşturulması için ise, çağırarak serileştirilmiş saat dilimi içeren bir dize almak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="c2b1f-113">Saat dilimi verileri seri durumdan çağırarak <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="c2b1f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2b1f-114">Example</span></span>

<span data-ttu-id="c2b1f-115">Aşağıdaki örnek çıkarır bir <xref:System.TimeZoneInfo> katıştırılmış .NET XML kaynak dosyasında depolanan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="c2b1f-116">Bu kod emin olmak için özel durum işleme gösterir bir <xref:System.TimeZoneInfo> uygulama tarafından gerekli nesne varsa.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="c2b1f-117">Örneği oluşturmak önce çalışır bir <xref:System.TimeZoneInfo> kayıt defteri kullanımından alma nesne <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="c2b1f-118">Saat dilimi örneği varsa, kodu katıştırılmış kaynak dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="c2b1f-119">Çünkü özel saat dilimleri için verileri (saat dilimleri kullanarak örneği <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi) depolanmadığı kayıt defterinde, kod arama <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Antarktika Palmer için saat dilimi örneği oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="c2b1f-120">Bunun yerine, hemen çağırmadan önce saat diliminin veri içeren bir dize almak için katıştırılmış kaynak dosyası görünüyor. <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c2b1f-121">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="c2b1f-121">Compiling the code</span></span>

<span data-ttu-id="c2b1f-122">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c2b1f-122">This example requires:</span></span>

* <span data-ttu-id="c2b1f-123">Bir başvuru System.Windows.Forms.dll ve System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="c2b1f-124">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="c2b1f-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="c2b1f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2b1f-125">See also</span></span>

<span data-ttu-id="c2b1f-126">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="c2b1f-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span></span>
