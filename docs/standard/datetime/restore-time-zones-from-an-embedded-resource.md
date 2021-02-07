---
description: 'Daha fazla bilgi edinin: nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
title: 'Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: 593fb392c073ca0a3b557b7d82d430b024b3d13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702489"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="2f281-103">Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="2f281-103">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="2f281-104">Bu konuda, bir kaynak dosyasına kaydedilmiş saat dilimlerinin nasıl geri yükleneceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f281-104">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="2f281-105">Saat dilimlerini kaydetme hakkında bilgi ve yönergeler için bkz. [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="2f281-105">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="2f281-106">Bir TimeZoneInfo nesnesinin katıştırılmış bir kaynaktan serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="2f281-106">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="2f281-107">Alınacak saat dilimi özel bir saat dilimi değilse, yöntemini kullanarak örneğini oluşturmaya çalışın <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f281-107">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="2f281-108"><xref:System.Resources.ResourceManager>Katıştırılmış kaynak dosyanın tam adını ve kaynak dosyasını içeren derlemeye bir başvuru geçirerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2f281-108">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="2f281-109">Gömülü kaynak dosyasının tam adını belirleyemeziz, derlemenin bildirimini incelemek için [Ildasm.exe (Il ayırıcı)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f281-109">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="2f281-110">Bir `.mresource` giriş, kaynağı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f281-110">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="2f281-111">Örnekte, kaynağın tam adı `SerializeTimeZoneData.SerializedTimeZones` .</span><span class="sxs-lookup"><span data-stu-id="2f281-111">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="2f281-112">Kaynak dosyası saat dilimi örnek oluşturma kodunu içeren bütünleştirilmiş koda katıştırılmışsa, `static` ( `Shared` Visual Basic) metodunu çağırarak buna bir başvuru alabilirsiniz <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f281-112">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="2f281-113">Yöntemine yapılan çağrı <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> başarısız olursa veya özel bir saat dilimi örneklenilmelidir, yöntemini çağırarak serileştirilmiş saat dilimini içeren bir dize alın <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2f281-113">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="2f281-114">Yöntemini çağırarak saat dilimi verilerinin serisini kaldırma <xref:System.TimeZoneInfo.FromSerializedString%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f281-114">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="2f281-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f281-115">Example</span></span>

<span data-ttu-id="2f281-116">Aşağıdaki örnek <xref:System.TimeZoneInfo> gömülü bir .NET XML kaynak dosyasında depolanan bir nesneyi seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="2f281-116">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="2f281-117">Bu kod <xref:System.TimeZoneInfo> , uygulamanın gerektirdiği bir nesnenin mevcut olduğundan emin olmak için özel durum işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f281-117">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="2f281-118">İlk olarak <xref:System.TimeZoneInfo> , yöntemini kullanarak kayıt defterinden alarak bir nesnesi örneğini oluşturmaya çalışır <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f281-118">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="2f281-119">Saat dilimi örneklenemez, kod onu katıştırılmış kaynak dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="2f281-119">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="2f281-120">Özel saat dilimlerinin (yöntemi kullanılarak oluşturulan saat dilimleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ) verileri kayıt defterinde depolanmadığı için, kod, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Palmer için saat dilimini oluşturmak üzere öğesini çağırmaz, Antarktika.</span><span class="sxs-lookup"><span data-stu-id="2f281-120">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="2f281-121">Bunun yerine, yöntemi çağırmadan önce saat diliminin verilerini içeren bir dizeyi almak için hemen gömülü kaynak dosyasına bakar <xref:System.TimeZoneInfo.FromSerializedString%2A> .</span><span class="sxs-lookup"><span data-stu-id="2f281-121">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2f281-122">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="2f281-122">Compiling the code</span></span>

<span data-ttu-id="2f281-123">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2f281-123">This example requires:</span></span>

- <span data-ttu-id="2f281-124">System.Windows.Forms.dll ve System.Core.dll bir başvuru projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="2f281-124">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="2f281-125">Aşağıdaki ad alanları içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="2f281-125">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="2f281-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f281-126">See also</span></span>

- [<span data-ttu-id="2f281-127">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="2f281-127">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="2f281-128">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="2f281-128">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="2f281-129">Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme</span><span class="sxs-lookup"><span data-stu-id="2f281-129">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
