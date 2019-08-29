---
title: 'Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme'
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
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107152"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="05251-102">Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme</span><span class="sxs-lookup"><span data-stu-id="05251-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="05251-103">Saat dilimi ile uyumlu bir uygulama genellikle belirli bir saat dilimi varlığını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="05251-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="05251-104">Ancak, tek tek <xref:System.TimeZoneInfo> nesnelerin kullanılabilirliği yerel sistemin kayıt defterinde depolanan bilgilere bağlı olduğundan, geleneksel kullanılabilir saat dilimleri de bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="05251-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="05251-105">Ayrıca, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan özel Saat dilimleriyle ilgili bilgiler, kayıt defterindeki diğer saat dilimi bilgileriyle depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="05251-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="05251-106">Bu saat dilimlerinin gerekli olmaları durumunda kullanılabilir olmasını sağlamak için bunları serileştirerek kaydedebilir ve daha sonra bunları seri durumdan kaldırarak geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05251-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="05251-107">Genellikle, bir <xref:System.TimeZoneInfo> nesneyi seri hale getirme zaman dilimi kullanan uygulamadan ayrı olarak meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="05251-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="05251-108">Seri hale getirilmiş <xref:System.TimeZoneInfo> nesneleri tutmak için kullanılan veri deposuna bağlı olarak, saat dilimi verileri bir kurulum veya yükleme yordamının parçası olarak (örneğin, verilerin kayıt defterinin bir uygulama anahtarında depolanması) veya çalışan bir yardımcı program yordamının bir parçası olarak serileştirilmeyebilir. son uygulama derlenmesinden önce (örneğin, serileştirilmiş veriler bir .NET XML kaynak (. resx) dosyasında depolandığında).</span><span class="sxs-lookup"><span data-stu-id="05251-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="05251-109">Uygulamayla derlenen bir kaynak dosyasına ek olarak, saat dilimi bilgileri için diğer birçok veri deposu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05251-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="05251-110">Bunlar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="05251-110">These include the following:</span></span>

- <span data-ttu-id="05251-111">Kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="05251-111">The registry.</span></span> <span data-ttu-id="05251-112">Bir uygulamanın, özel saat dilimi verilerini depolamak için, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgelerinin alt anahtarlarını kullanmak yerine kendi uygulama anahtarının alt anahtarlarını kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="05251-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

- <span data-ttu-id="05251-113">Yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="05251-113">Configuration files.</span></span>

- <span data-ttu-id="05251-114">Diğer sistem dosyaları.</span><span class="sxs-lookup"><span data-stu-id="05251-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="05251-115">Bir saat dilimini bir. resx dosyasına serileştirerek kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="05251-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="05251-116">Mevcut bir saat dilimini alın veya yeni bir saat dilimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05251-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="05251-117">Mevcut bir saat dilimini almak için bkz [. nasıl yapılır: Önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine](../../../docs/standard/datetime/access-utc-and-local.md) erişin ve [şunları yapın: Bir TimeZoneInfo nesnesi](../../../docs/standard/datetime/instantiate-time-zone-info.md)örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05251-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="05251-118">Yeni bir saat dilimi oluşturmak için, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yönteminin aşırı yüklemelerinin birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="05251-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="05251-119">Daha fazla bilgi için [nasıl yapılır: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) olmadan saat dilimleri oluşturun ve [şunları yapın: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)ile saat dilimleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05251-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="05251-120">Saat diliminin verilerini içeren bir dize oluşturmak için yönteminiçağırın.<xref:System.TimeZoneInfo.ToSerializedString%2A></span><span class="sxs-lookup"><span data-stu-id="05251-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="05251-121">Ad ve <xref:System.IO.StreamWriter> isteğe bağlı olarak. resx dosyasının <xref:System.IO.StreamWriter> yolunu, sınıf oluşturucusuna ekleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05251-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="05251-122"><xref:System.IO.StreamWriter> <xref:System.Resources.ResXResourceWriter> Nesneyi<xref:System.Resources.ResXResourceWriter> sınıf oluşturucusuna geçirerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05251-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="05251-123">Saat diliminin serileştirilmiş dizesini <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="05251-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="05251-124">Çağrı <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05251-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="05251-125">Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05251-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="05251-126">Yöntemini çağırarak nesneyi kapatın. <xref:System.IO.StreamWriter> <xref:System.IO.StreamWriter.Close%2A></span><span class="sxs-lookup"><span data-stu-id="05251-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="05251-127">Oluşturulan. resx dosyasını uygulamanın Visual Studio projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05251-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="05251-128">Visual Studio 'da **Özellikler** penceresini kullanarak,. resx dosyasının **derleme eylemi** özelliğinin **gömülü kaynak**olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="05251-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="05251-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="05251-129">Example</span></span>

<span data-ttu-id="05251-130">Aşağıdaki örnek, merkezi standart saati <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo> ve Palmer istasyonunu temsil eden bir nesneyi, Antarktika zaman SerializedTimeZones. resx adlı bir .NET XML kaynak dosyasına temsil eden bir nesneyi seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="05251-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="05251-131">Merkezi Standart saat genellikle kayıt defterinde tanımlanır; Palmer Istasyonu, Antarktika özel bir saat dilimsidir.</span><span class="sxs-lookup"><span data-stu-id="05251-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="05251-132">Bu örnek, derleme <xref:System.TimeZoneInfo> zamanında bir kaynak dosyasında kullanılabilmesi için nesneleri seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="05251-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="05251-133"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> Yöntemi bir .NET XML kaynak dosyasına tüm başlık bilgilerini eklediğinden, mevcut bir dosyaya kaynak eklemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="05251-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="05251-134">Bu örnek, SerializedTimeZones. resx dosyasını denetleyerek ve varsa, iki serileştirilmiş zaman dilimi dışındaki tüm kaynaklarını genel <xref:System.Collections.Generic.Dictionary%602> bir nesneye depolayarak bunu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="05251-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="05251-135">Varolan dosya daha sonra silinir ve var olan kaynaklar yeni bir SerializedTimeZones. resx dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="05251-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="05251-136">Seri hale getirilmiş saat dilimi verileri de bu dosyaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="05251-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="05251-137">Kaynakların anahtar (veya **ad**) alanları, gömülü boşluklar içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="05251-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="05251-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> Yöntemi, kaynak dosyasına atanmadan önce saat dilimi tanımlayıcılarında tüm gömülü boşlukları kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="05251-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="05251-139">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="05251-139">Compiling the code</span></span>

<span data-ttu-id="05251-140">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="05251-140">This example requires:</span></span>

- <span data-ttu-id="05251-141">System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="05251-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="05251-142">Aşağıdaki ad alanları içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="05251-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="05251-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05251-143">See also</span></span>

- [<span data-ttu-id="05251-144">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="05251-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="05251-145">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="05251-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="05251-146">Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="05251-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
