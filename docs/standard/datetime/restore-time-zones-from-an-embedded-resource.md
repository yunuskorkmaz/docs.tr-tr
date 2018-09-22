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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99d38b336b5e655dd1c96682eec90c5fbe8469d6
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562736"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="427ab-102">Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="427ab-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="427ab-103">Bu konuda, bir kaynak dosyasında kaydedilen saat dilimlerini geri yükleme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="427ab-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="427ab-104">Bilgi ve saat dilimlerini kaydetme hakkında yönergeler için bkz. [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="427ab-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="427ab-105">Katıştırılmış bir kaynaktan bir Timezoneınfo nesnesinin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="427ab-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="427ab-106">Kullanarak örneği oluşturmak saat dilimini alınacak özel bir saat dilimi değilse deneyin <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="427ab-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="427ab-107">Örneği bir <xref:System.Resources.ResourceManager> katıştırılmış kaynak dosyasını ve kaynak dosyasını içeren derlemeyi bir başvuru tam olarak nitelenmiş adını geçirerek nesne.</span><span class="sxs-lookup"><span data-stu-id="427ab-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="427ab-108">Katıştırılmış kaynak dosyasının tam adı belirleyemiyorsa, kullanın [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derlemenin bildirimi incelemek için.</span><span class="sxs-lookup"><span data-stu-id="427ab-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="427ab-109">Bir `.mresource` girdisini tanımlayan kaynak.</span><span class="sxs-lookup"><span data-stu-id="427ab-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="427ab-110">Örnekte, kaynağın tam adıdır `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="427ab-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="427ab-111">Saat dilimi örnekleme kodunu içeren aynı derlemede katıştırılmış kaynak dosyası ise çağırarak ona bir başvuru alabilirsiniz `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="427ab-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="427ab-112">Çağrı <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodu başarısız olursa veya özel bir saat dilimi örneği varsa çağırarak serileştirilmiş saat dilimini içeren bir dize almak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="427ab-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="427ab-113">Saat dilimi veri çağırarak seri durumdan <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="427ab-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="427ab-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="427ab-114">Example</span></span>

<span data-ttu-id="427ab-115">Aşağıdaki örnek seri durumdan çıkarır bir <xref:System.TimeZoneInfo> katıştırılmış bir .NET XML kaynak dosyasında depolanan nesne.</span><span class="sxs-lookup"><span data-stu-id="427ab-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="427ab-116">Bu kod emin olmak için özel durum işleme gösterir bir <xref:System.TimeZoneInfo> uygulamanın gerektirdiği nesne.</span><span class="sxs-lookup"><span data-stu-id="427ab-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="427ab-117">İlk örneği çalışan bir <xref:System.TimeZoneInfo> kullanarak kayıt defteri alarak nesne <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="427ab-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="427ab-118">Saat dilimi oluşturulamaz, kodu katıştırılmış kaynak dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="427ab-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="427ab-119">Çünkü veri özel saat dilimi için (saat dilimlerini kullanarak örneği oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi) depolanmadığı kayıt defterinde, kod arama <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> saat dilimini Palmer, Antarktika örneklemek için.</span><span class="sxs-lookup"><span data-stu-id="427ab-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="427ab-120">Bunun yerine, katıştırılmış kaynak dosyasına çağırmadan önce saat diliminin verileri içeren bir dizeyi almak için hemen görünür <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="427ab-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="427ab-121">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="427ab-121">Compiling the code</span></span>

<span data-ttu-id="427ab-122">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="427ab-122">This example requires:</span></span>

* <span data-ttu-id="427ab-123">Projeye bir başvuru System.Windows.Forms.dll ve System.Core.dll eklenmesi gerektiğini.</span><span class="sxs-lookup"><span data-stu-id="427ab-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="427ab-124">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="427ab-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="427ab-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="427ab-125">See also</span></span>

* [<span data-ttu-id="427ab-126">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="427ab-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="427ab-127">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="427ab-127">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
* [<span data-ttu-id="427ab-128">Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme</span><span class="sxs-lookup"><span data-stu-id="427ab-128">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
