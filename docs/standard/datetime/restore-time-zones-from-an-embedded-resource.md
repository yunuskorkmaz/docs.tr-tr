---
title: 'Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: cd2119d6d22f3f676b7167ed545aeb058123cfb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122197"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="2551b-102">Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="2551b-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="2551b-103">Bu konuda, bir kaynak dosyasına kaydedilmiş saat dilimlerinin nasıl geri yükleneceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2551b-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="2551b-104">Saat dilimlerini kaydetme hakkında bilgi ve yönergeler için bkz. [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="2551b-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="2551b-105">Bir TimeZoneInfo nesnesinin katıştırılmış bir kaynaktan serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="2551b-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="2551b-106">Alınacak saat dilimi özel bir saat dilimi değilse, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodunu kullanarak örneğini oluşturmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="2551b-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="2551b-107">Katıştırılmış kaynak dosyasının tam adını ve kaynak dosyasını içeren derlemeye bir başvuru geçirerek bir <xref:System.Resources.ResourceManager> nesnesi örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2551b-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="2551b-108">Gömülü kaynak dosyasının tam adını belirleyemeziz, derlemenin bildirimini incelemek için [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2551b-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="2551b-109">Bir `.mresource` girdisi kaynağı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2551b-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="2551b-110">Örnekte, kaynağın tam adı `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="2551b-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="2551b-111">Kaynak dosyası saat dilimi örnek oluşturma kodunu içeren bütünleştirilmiş koda katıştırılmışsa, `static` (`Shared` Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemini çağırarak buna bir başvuru alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2551b-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="2551b-112"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemine yapılan çağrı başarısız olursa veya özel bir saat dilimi örneklenilmelidir, <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemini çağırarak serileştirilmiş saat dilimini içeren bir dize alın.</span><span class="sxs-lookup"><span data-stu-id="2551b-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="2551b-113"><xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemini çağırarak saat dilimi verilerinin serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="2551b-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="2551b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="2551b-114">Example</span></span>

<span data-ttu-id="2551b-115">Aşağıdaki örnek gömülü bir .NET XML kaynak dosyasında depolanan bir <xref:System.TimeZoneInfo> nesnesini serileştirir.</span><span class="sxs-lookup"><span data-stu-id="2551b-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="2551b-116">Bu kod, uygulamanın gerektirdiği bir <xref:System.TimeZoneInfo> nesnesinin mevcut olduğundan emin olmak için özel durum işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2551b-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="2551b-117">İlk olarak, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodunu kullanarak kayıt defterinden alarak bir <xref:System.TimeZoneInfo> nesnesi örneğini oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="2551b-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="2551b-118">Saat dilimi örneklenemez, kod onu katıştırılmış kaynak dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="2551b-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="2551b-119">Özel saat dilimlerinin (<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan saat dilimleri) verileri kayıt defterinde depolanmadığı için, kod, Palmer, Antarktika için saat dilimini başlatmak üzere <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="2551b-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="2551b-120">Bunun yerine, <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemini çağırmadan önce saat diliminin verilerini içeren bir dizeyi almak için hemen gömülü kaynak dosyasına bakar.</span><span class="sxs-lookup"><span data-stu-id="2551b-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2551b-121">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="2551b-121">Compiling the code</span></span>

<span data-ttu-id="2551b-122">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2551b-122">This example requires:</span></span>

- <span data-ttu-id="2551b-123">System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="2551b-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="2551b-124">Aşağıdaki ad alanları içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="2551b-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="2551b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2551b-125">See also</span></span>

- [<span data-ttu-id="2551b-126">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="2551b-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="2551b-127">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="2551b-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="2551b-128">Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme</span><span class="sxs-lookup"><span data-stu-id="2551b-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
