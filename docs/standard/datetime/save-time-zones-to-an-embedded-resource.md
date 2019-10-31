---
title: 'Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme'
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
ms.openlocfilehash: aaee4e82d09e8b604d06dadb5a5eefe8d2e1f307
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123769"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="0ae82-102">Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme</span><span class="sxs-lookup"><span data-stu-id="0ae82-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="0ae82-103">Saat dilimi ile uyumlu bir uygulama genellikle belirli bir saat dilimi varlığını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="0ae82-104">Ancak, bireysel <xref:System.TimeZoneInfo> nesnelerinin kullanılabilirliği yerel sistemin kayıt defterinde depolanan bilgilere bağlı olduğundan, geleneksel kullanılabilir saat dilimleri de bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="0ae82-105">Ayrıca, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan özel Saat dilimleriyle ilgili bilgiler, kayıt defterindeki diğer saat dilimi bilgileriyle depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="0ae82-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="0ae82-106">Bu saat dilimlerinin gerekli olmaları durumunda kullanılabilir olmasını sağlamak için bunları serileştirerek kaydedebilir ve daha sonra bunları seri durumdan kaldırarak geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ae82-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="0ae82-107">Genellikle, bir <xref:System.TimeZoneInfo> nesnesini seri hale getirme zaman dilimi kullanan uygulamadan ayrı olur.</span><span class="sxs-lookup"><span data-stu-id="0ae82-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="0ae82-108">Seri hale getirilmiş <xref:System.TimeZoneInfo> nesnelerini tutmak için kullanılan veri deposuna bağlı olarak, saat dilimi verileri bir kurulum veya yükleme yordamının parçası olarak (örneğin, verilerin kayıt defterinin bir uygulama anahtarında depolanması) veya daha önce çalışan bir yardımcı program yordamının bir parçası olarak seri hale getirilebilir. son uygulama derlenir (örneğin, serileştirilmiş veriler bir .NET XML kaynak (. resx) dosyasında depolandığında).</span><span class="sxs-lookup"><span data-stu-id="0ae82-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="0ae82-109">Uygulamayla derlenen bir kaynak dosyasına ek olarak, saat dilimi bilgileri için diğer birçok veri deposu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="0ae82-110">Bunlar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="0ae82-110">These include the following:</span></span>

- <span data-ttu-id="0ae82-111">Kayıt defteri.</span><span class="sxs-lookup"><span data-stu-id="0ae82-111">The registry.</span></span> <span data-ttu-id="0ae82-112">Bir uygulamanın, özel saat dilimi verilerini depolamak için, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time bölgelerinin alt anahtarlarını kullanmak yerine kendi uygulama anahtarının alt anahtarlarını kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0ae82-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

- <span data-ttu-id="0ae82-113">Yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="0ae82-113">Configuration files.</span></span>

- <span data-ttu-id="0ae82-114">Diğer sistem dosyaları.</span><span class="sxs-lookup"><span data-stu-id="0ae82-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="0ae82-115">Bir saat dilimini bir. resx dosyasına serileştirerek kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="0ae82-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="0ae82-116">Mevcut bir saat dilimini alın veya yeni bir saat dilimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ae82-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="0ae82-117">Mevcut bir saat dilimini almak için bkz. [nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](../../../docs/standard/datetime/access-utc-and-local.md) ve [nasıl yapılır: bir TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="0ae82-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="0ae82-118">Yeni bir saat dilimi oluşturmak için <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yönteminin aşırı yüklemelerinin birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0ae82-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="0ae82-119">Daha fazla bilgi için bkz. [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları Ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="0ae82-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="0ae82-120">Saat diliminin verilerini içeren bir dize oluşturmak için <xref:System.TimeZoneInfo.ToSerializedString%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0ae82-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="0ae82-121">Adı ve isteğe bağlı olarak. resx dosyasının yolunu <xref:System.IO.StreamWriter> sınıf oluşturucusuna girerek bir <xref:System.IO.StreamWriter> nesnesi örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ae82-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="0ae82-122"><xref:System.IO.StreamWriter> nesnesini <xref:System.Resources.ResXResourceWriter> sınıf oluşturucusuna geçirerek bir <xref:System.Resources.ResXResourceWriter> nesnesi örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ae82-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="0ae82-123">Saat dilimini serileştirilmiş dizeyi <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="0ae82-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="0ae82-124"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0ae82-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="0ae82-125"><xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0ae82-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="0ae82-126"><xref:System.IO.StreamWriter> nesnesini <xref:System.IO.StreamWriter.Close%2A> yöntemini çağırarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="0ae82-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="0ae82-127">Oluşturulan. resx dosyasını uygulamanın Visual Studio projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0ae82-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="0ae82-128">Visual Studio 'da **Özellikler** penceresini kullanarak,. resx dosyasının **derleme eylemi** özelliğinin **gömülü kaynak**olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="0ae82-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="0ae82-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ae82-129">Example</span></span>

<span data-ttu-id="0ae82-130">Aşağıdaki örnek, SerializedTimeZones. resx adlı bir .NET XML kaynak dosyasına Antarktika zamanını temsil eden merkezi standart saatini ve bir <xref:System.TimeZoneInfo> nesnesini temsil eden bir <xref:System.TimeZoneInfo> nesnesini seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="0ae82-131">Merkezi Standart saat genellikle kayıt defterinde tanımlanır; Palmer Istasyonu, Antarktika özel bir saat dilimsidir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="0ae82-132">Bu örnek, derleme zamanında bir kaynak dosyasında kullanılabilmesi için nesneleri <xref:System.TimeZoneInfo> seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="0ae82-133"><xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> yöntemi bir .NET XML kaynak dosyasına tüm başlık bilgilerini eklediğinden, mevcut bir dosyaya kaynak eklemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ae82-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="0ae82-134">Örnek, SerializedTimeZones. resx dosyasını denetleyerek ve varsa, iki seri hale getirilmiş zaman dilimi dışındaki tüm kaynaklarını genel bir <xref:System.Collections.Generic.Dictionary%602> nesnesine depolayarak bunu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="0ae82-135">Varolan dosya daha sonra silinir ve var olan kaynaklar yeni bir SerializedTimeZones. resx dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="0ae82-136">Seri hale getirilmiş saat dilimi verileri de bu dosyaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="0ae82-137">Kaynakların anahtar (veya **ad**) alanları, gömülü boşluklar içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="0ae82-138"><xref:System.String.Replace%28System.String%2CSystem.String%29> yöntemi, kaynak dosyasına atanmadan önce saat dilimi tanımlayıcılarında tüm gömülü boşlukları kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0ae82-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="0ae82-139">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="0ae82-139">Compiling the code</span></span>

<span data-ttu-id="0ae82-140">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0ae82-140">This example requires:</span></span>

- <span data-ttu-id="0ae82-141">System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ae82-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="0ae82-142">Aşağıdaki ad alanları içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="0ae82-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0ae82-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ae82-143">See also</span></span>

- [<span data-ttu-id="0ae82-144">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="0ae82-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="0ae82-145">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="0ae82-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="0ae82-146">Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme</span><span class="sxs-lookup"><span data-stu-id="0ae82-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
