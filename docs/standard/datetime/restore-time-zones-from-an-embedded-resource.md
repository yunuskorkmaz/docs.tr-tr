---
title: 'Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98813bf6685be78d33ebd5cc5e8c07a61a811c25
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106759"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="09172-102">Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="09172-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="09172-103">Bu konuda, bir kaynak dosyasına kaydedilmiş saat dilimlerinin nasıl geri yükleneceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="09172-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="09172-104">Saat dilimlerini kaydetme hakkında bilgi ve yönergeler için bkz [. nasıl yapılır: Zaman dilimlerini gömülü bir kaynağa](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)kaydedin.</span><span class="sxs-lookup"><span data-stu-id="09172-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="09172-105">Bir TimeZoneInfo nesnesinin katıştırılmış bir kaynaktan serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="09172-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="09172-106">Alınacak saat dilimi özel bir saat dilimi değilse, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemini kullanarak örneğini oluşturmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="09172-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="09172-107">Katıştırılmış kaynak <xref:System.Resources.ResourceManager> dosyanın tam adını ve kaynak dosyasını içeren derlemeye bir başvuru geçirerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="09172-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="09172-108">Gömülü kaynak dosyasının tam adını belirleyemeziz, derlemenin bildirimini incelemek için [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="09172-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="09172-109">Bir `.mresource` giriş, kaynağı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="09172-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="09172-110">Örnekte, kaynağın tam adı `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="09172-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="09172-111">Kaynak dosyası saat dilimi örnek oluşturma kodunu içeren bütünleştirilmiş koda katıştırılmışsa, `static` (`Shared` Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metodunu çağırarak buna bir başvuru alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09172-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="09172-112"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Yöntemine yapılan çağrı başarısız olursa veya özel bir saat dilimi örneklenilmelidir, <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemini çağırarak serileştirilmiş saat dilimini içeren bir dize alın.</span><span class="sxs-lookup"><span data-stu-id="09172-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="09172-113"><xref:System.TimeZoneInfo.FromSerializedString%2A> Yöntemini çağırarak saat dilimi verilerinin serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="09172-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="09172-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="09172-114">Example</span></span>

<span data-ttu-id="09172-115">Aşağıdaki örnek gömülü bir .NET XML kaynak <xref:System.TimeZoneInfo> dosyasında depolanan bir nesneyi seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="09172-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="09172-116">Bu kod, uygulamanın gerektirdiği bir <xref:System.TimeZoneInfo> nesnenin mevcut olduğundan emin olmak için özel durum işleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="09172-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="09172-117">İlk olarak, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemini kullanarak kayıt <xref:System.TimeZoneInfo> defterinden alarak bir nesnesi örneğini oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="09172-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="09172-118">Saat dilimi örneklenemez, kod onu katıştırılmış kaynak dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="09172-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="09172-119">Özel saat dilimlerinin ( <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan saat dilimleri) verileri kayıt defterinde depolanmadığı için, kod, Palmer için saat dilimini oluşturmak <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> üzere öğesini çağırmaz, Antarktika.</span><span class="sxs-lookup"><span data-stu-id="09172-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="09172-120">Bunun yerine, <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi çağırmadan önce saat diliminin verilerini içeren bir dizeyi almak için hemen gömülü kaynak dosyasına bakar.</span><span class="sxs-lookup"><span data-stu-id="09172-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="09172-121">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="09172-121">Compiling the code</span></span>

<span data-ttu-id="09172-122">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="09172-122">This example requires:</span></span>

- <span data-ttu-id="09172-123">System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="09172-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="09172-124">Aşağıdaki ad alanları içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="09172-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="09172-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09172-125">See also</span></span>

- [<span data-ttu-id="09172-126">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="09172-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="09172-127">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="09172-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="09172-128">Nasıl yapılır: Zaman dilimlerini gömülü bir kaynağa Kaydet</span><span class="sxs-lookup"><span data-stu-id="09172-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
