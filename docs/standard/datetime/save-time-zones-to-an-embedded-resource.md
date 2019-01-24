---
title: 'Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592880"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="7d81e-102">Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme</span><span class="sxs-lookup"><span data-stu-id="7d81e-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="7d81e-103">Genellikle saat dilimiyle uyumlu bir uygulama belirli bir saat dilimini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d81e-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="7d81e-104">Ancak, çünkü tek kullanılabilirliğini <xref:System.TimeZoneInfo> yerel sisteminin kayıt defterinde depolanan bilgileri bağımlı nesneler, Alışıldığı bile kullanılabilir saat dilimi yok.</span><span class="sxs-lookup"><span data-stu-id="7d81e-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="7d81e-105">Ayrıca, özel saat dilimleri hakkında bilgi örneği kullanarak <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi ile diğer saat dilimi bilgileri kayıt depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="7d81e-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="7d81e-106">Gerektiğinde bu saat dilimlerini kullanılabilir olmasını sağlamak için seri hale getirme tarafından kaydedin ve daha sonra seri durumdan çıkarılırken tarafından geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d81e-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="7d81e-107">Genellikle, seri hale getirilirken bir <xref:System.TimeZoneInfo> nesne saat dilimiyle uyumlu uygulama dışında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7d81e-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="7d81e-108">Seri hale getirilmiş tutmak için kullanılan veri deposu bağlı olarak <xref:System.TimeZoneInfo> nesneler, saat dilimi veri seri hale getirilemiyor bir kurulum veya yükleme yordamı (örneğin, veriler bir uygulama kayıt defteri anahtarında depolanır) bir parçası olarak ya da çalışan bir yardımcı programı yordamının parçası olarak son uygulama (örneğin, serileştirilmiş veriler .NET XML kaynak (.resx) dosyası depolandığında) derlenmeden önce.</span><span class="sxs-lookup"><span data-stu-id="7d81e-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="7d81e-109">Uygulama ile derlenmiş olan bir kaynak dosyasına ek olarak, çeşitli veri depoları için saat dilimi bilgileri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d81e-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="7d81e-110">Bunlar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="7d81e-110">These include the following:</span></span>

* <span data-ttu-id="7d81e-111">Kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="7d81e-111">The registry.</span></span> <span data-ttu-id="7d81e-112">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgeleri anahtarlarını kullanmak yerine özel saat dilimi veri depolamak için bir uygulama anahtarlarını kendi uygulama anahtarı kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7d81e-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="7d81e-113">Yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="7d81e-113">Configuration files.</span></span>

* <span data-ttu-id="7d81e-114">Diğer sistem dosyaları.</span><span class="sxs-lookup"><span data-stu-id="7d81e-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="7d81e-115">Bir .resx dosyasına serileştirmek tarafından bir saat dilimi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="7d81e-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="7d81e-116">Var olan bir saat dilimi almak veya yeni bir saat dilimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d81e-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="7d81e-117">Var olan bir saat dilimi almak için bkz: [nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md) ve [nasıl yapılır: Bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="7d81e-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="7d81e-118">Yeni bir saat dilimi oluşturmak amacıyla bir aşırı yüklemelerinden birini çağırın <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d81e-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="7d81e-119">Daha fazla bilgi için [nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="7d81e-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="7d81e-120">Çağrı <xref:System.TimeZoneInfo.ToSerializedString%2A> saat diliminin veri içeren bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d81e-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="7d81e-121">Örneği bir <xref:System.IO.StreamWriter> nesne adı ve isteğe bağlı olarak için .resx dosyasının yolunu sağlayarak <xref:System.IO.StreamWriter> sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="7d81e-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="7d81e-122">Örneği bir <xref:System.Resources.ResXResourceWriter> geçirerek nesne <xref:System.IO.StreamWriter> nesnesini <xref:System.Resources.ResXResourceWriter> sınıf oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="7d81e-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="7d81e-123">Geçişi saat dilimine ait dize olarak serileştirilmiş <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d81e-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="7d81e-124">Çağrı <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d81e-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="7d81e-125">Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d81e-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="7d81e-126">Kapat <xref:System.IO.StreamWriter> çağırarak kendi <xref:System.IO.StreamWriter.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d81e-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="7d81e-127">Oluşturulan bir .resx dosyası, uygulamanın Visual Studio projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d81e-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="7d81e-128">Kullanarak **özellikleri** Visual Studio penceresinde emin olun, .resx dosyasının **derleme eylemi** özelliği **gömülü kaynak**.</span><span class="sxs-lookup"><span data-stu-id="7d81e-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="7d81e-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d81e-129">Example</span></span>

<span data-ttu-id="7d81e-130">Aşağıdaki örnek serileştiren bir <xref:System.TimeZoneInfo> Orta Standart Saati temsil eden nesne ve <xref:System.TimeZoneInfo> SerializedTimeZones.resx adlı bir .NET XML kaynak dosyası Palmer istasyonu, Antarktika zamanı temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7d81e-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="7d81e-131">Orta Standart Saati, genellikle kayıt defterinde tanımlanır; PALMER istasyonu, Antarktika, özel bir zaman dilimi olur.</span><span class="sxs-lookup"><span data-stu-id="7d81e-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="7d81e-132">Bu örnekte serileştiren <xref:System.TimeZoneInfo> bunlar bir kaynak dosyasında derleme zamanında kullanılabilir olacak şekilde nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7d81e-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="7d81e-133">Çünkü <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi .NET XML kaynak dosyası için tam başlık bilgilerini ekler, kaynakları var olan bir dosyaya eklemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d81e-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="7d81e-134">Örnek için SerializedTimeZones.resx dosyasını denetleyerek bu işler ve, varsa, tüm kaynaklarını dışında depolama iki saat dilimleri için genel serileştirilmiş <xref:System.Collections.Generic.Dictionary%602> nesne.</span><span class="sxs-lookup"><span data-stu-id="7d81e-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="7d81e-135">Var olan dosyayı ardından silinir ve mevcut kaynakları yeni SerializedTimeZones.resx dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="7d81e-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="7d81e-136">Seri hale getirilmiş saat dilimi veri bu dosyaya da eklenir.</span><span class="sxs-lookup"><span data-stu-id="7d81e-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="7d81e-137">Anahtar (veya **adı**) kaynakları alanlarının gömülü boşluklar içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="7d81e-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="7d81e-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Yöntemi, kaynak dosyasına atanmadan önce tüm gömülü boşluklar saat dilimi tanımlayıcıları kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7d81e-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="7d81e-139">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="7d81e-139">Compiling the code</span></span>

<span data-ttu-id="7d81e-140">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7d81e-140">This example requires:</span></span>

* <span data-ttu-id="7d81e-141">Projeye bir başvuru System.Windows.Forms.dll ve System.Core.dll eklenmesi gerektiğini.</span><span class="sxs-lookup"><span data-stu-id="7d81e-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="7d81e-142">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="7d81e-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="7d81e-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d81e-143">See also</span></span>

- [<span data-ttu-id="7d81e-144">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="7d81e-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="7d81e-145">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7d81e-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="7d81e-146">Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="7d81e-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
