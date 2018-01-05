---
title: "Nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme"
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
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93dfc62df1c1d68e09a3734402924bbac1a074cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="71d25-102">Nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme</span><span class="sxs-lookup"><span data-stu-id="71d25-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="71d25-103">Saat dilimi algılayan uygulama genelde belirli bir saat dilimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="71d25-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="71d25-104">Ancak, çünkü tek kullanılabilirliğini <xref:System.TimeZoneInfo> yerel sistemin kayıt defterinde depolanan bilgileri bağımlı nesneler, geleneksel olarak bile kullanılabilir saat dilimi yok.</span><span class="sxs-lookup"><span data-stu-id="71d25-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="71d25-105">Ayrıca, özel saat dilimleri hakkında bilgi örneği kullanarak <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi, kayıt defterinde diğer saat dilimi bilgileri ile depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="71d25-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="71d25-106">Gerektiğinde bu saat dilimleri kullanılabilir olduğundan emin olmak için seri hale getirme tarafından kaydedebilir ve daha sonra bunları seri durumdan çıkarılırken tarafından geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="71d25-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="71d25-107">Genellikle, seri hale getirilirken bir <xref:System.TimeZoneInfo> nesne dışında saat dilimi algılayan uygulama oluşur.</span><span class="sxs-lookup"><span data-stu-id="71d25-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="71d25-108">Serileştirilmiş tutmak için kullanılan veri deposu bağlı olarak <xref:System.TimeZoneInfo> nesneleri, saat dilimi veri serileştirilmiş Kurulum veya yükleme yordamı (örneğin, bir uygulama kayıt defteri anahtarında veri depolandığında) bir parçası olarak ya da çalışan bir yardımcı programı yordamının parçası olarak son uygulama (örneğin, serileştirilmiş veriler bir .NET XML kaynak (.resx) dosyasında depolandığında) derlenmiş önce.</span><span class="sxs-lookup"><span data-stu-id="71d25-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="71d25-109">Uygulama ile derlenen bir kaynak dosyasına ek olarak, diğer birkaç veri depoları için saat dilimi bilgilerini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71d25-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="71d25-110">Bunlar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="71d25-110">These include the following:</span></span>

* <span data-ttu-id="71d25-111">Kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="71d25-111">The registry.</span></span> <span data-ttu-id="71d25-112">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones alt anahtarları kullanmak yerine özel saat dilimi veri depolamak için uygulamanın kendi uygulama anahtarı alt anahtarları kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="71d25-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="71d25-113">Yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="71d25-113">Configuration files.</span></span>

* <span data-ttu-id="71d25-114">Diğer sistem dosyalarını.</span><span class="sxs-lookup"><span data-stu-id="71d25-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="71d25-115">Bir saat dilimi .resx dosyasına serileştirme tarafından kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="71d25-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="71d25-116">Varolan bir saat dilimi almak veya yeni bir saat dilimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71d25-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="71d25-117">Varolan bir saat dilimi almak için bkz: [nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md) ve [nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="71d25-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="71d25-118">Yeni bir saat dilimi oluşturmak için aşırı birini çağırın <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71d25-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="71d25-119">Daha fazla bilgi için bkz: [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="71d25-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="71d25-120">Çağrı <xref:System.TimeZoneInfo.ToSerializedString%2A> saat diliminin veri içeren bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71d25-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="71d25-121">Örneği bir <xref:System.IO.StreamWriter> ad ve isteğe bağlı olarak için .resx dosyasının yolunu sağlayarak nesne <xref:System.IO.StreamWriter> sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="71d25-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="71d25-122">Örneği bir <xref:System.Resources.ResXResourceWriter> geçirerek nesne <xref:System.IO.StreamWriter> nesnesine <xref:System.Resources.ResXResourceWriter> sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="71d25-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="71d25-123">Geçişi saat dilimi 's dize olarak serileştirilmiş <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71d25-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="71d25-124">Çağrı <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71d25-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="71d25-125">Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71d25-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="71d25-126">Kapat <xref:System.IO.StreamWriter> çağırarak nesne kendi <xref:System.IO.StreamWriter.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71d25-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="71d25-127">Oluşturulan .resx dosyası uygulamanın Visual Studio projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71d25-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="71d25-128">Kullanarak **özellikleri** Visual Studio'da pencere emin olun .resx dosyanın **yapı eylemi** özelliği ayarlanmış **katıştırılmış kaynak**.</span><span class="sxs-lookup"><span data-stu-id="71d25-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="71d25-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="71d25-129">Example</span></span>

<span data-ttu-id="71d25-130">Aşağıdaki örnek serileştiren bir <xref:System.TimeZoneInfo> Orta Standart Saati temsil eden nesnesi ve <xref:System.TimeZoneInfo> SerializedTimeZones.resx adlı bir .NET XML kaynak dosyası Palmer istasyon, Antarktika saati temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="71d25-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="71d25-131">Orta Standart Saati kayıt defterinde tanımlanır; PALMER istasyon, Antarktika özel bir saat dilimi olur.</span><span class="sxs-lookup"><span data-stu-id="71d25-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="71d25-132">Bu örnek serileştiren <xref:System.TimeZoneInfo> böylece bunlar kaynak dosyası derleme zamanında kullanılabilir nesneleri.</span><span class="sxs-lookup"><span data-stu-id="71d25-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="71d25-133">Çünkü <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi, bir .NET XML kaynak dosyasına tam üst bilgileri ekler, kaynaklar için varolan bir dosyayı eklemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="71d25-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="71d25-134">Örnek için SerializedTimeZones.resx dosyasını denetleyerek bu işler ve, varsa, kaynaklarının tümü dışında depolama iki saat dilimleri için genel seri <xref:System.Collections.Generic.Dictionary%602> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="71d25-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="71d25-135">Var olan dosyayı ardından silinir ve var olan kaynaklar için yeni bir SerializedTimeZones.resx dosyası eklenir.</span><span class="sxs-lookup"><span data-stu-id="71d25-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="71d25-136">Serileştirilmiş saat dilimi verilerini de bu dosyaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="71d25-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="71d25-137">Anahtar (veya **adı**) kaynakları alanlarının katıştırılmış boşluklar içeremez.</span><span class="sxs-lookup"><span data-stu-id="71d25-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="71d25-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Yöntemi kaynak dosyasına atanan önce tüm katıştırılmış boşluklar saat dilimi tanımlayıcıları kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="71d25-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="71d25-139">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="71d25-139">Compiling the code</span></span>

<span data-ttu-id="71d25-140">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="71d25-140">This example requires:</span></span>

* <span data-ttu-id="71d25-141">Bir başvuru System.Windows.Forms.dll ve System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="71d25-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="71d25-142">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="71d25-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="71d25-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71d25-143">See also</span></span>

<span data-ttu-id="71d25-144">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="71d25-144">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span></span>
