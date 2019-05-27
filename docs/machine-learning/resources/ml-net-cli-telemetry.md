---
title: ML.NET CLI tarafından telemetri toplama
description: Analiz için bilgileri, hangi verileri toplanır ve bunu devre dışı bırakma, kullanım verileri toplayan ML.NET CLI telemetri özellikler hakkında bilgi edinin. Ayrıca .NET lisans sözleşmesi ve Microsoft GDPR uyumluluğu hakkında bilgi için bağlantılar öğrenin.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 94c66267dfeec4b70ba4dd1fc47518eb0e01509a
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053584"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="b0768-104">ML.NET CLI tarafından telemetri toplama</span><span class="sxs-lookup"><span data-stu-id="b0768-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="b0768-105">[ML.NET CLI](http://aka.ms/mlnet-cli) kullanmak için Microsoft tarafından toplanan anonim kullanım verileri toplayan telemetri özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="b0768-105">The [ML.NET CLI](http://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="b0768-106">Microsoft verileri nasıl kullanır</span><span class="sxs-lookup"><span data-stu-id="b0768-106">How Microsoft uses the data</span></span>

<span data-ttu-id="b0768-107">Ürün ekibine araçları geliştirmek nasıl anlamanıza yardımcı olması için ML.NET CLI telemetri verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0768-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="b0768-108">Örneğin, müşteriler seyrek belirli bir makine öğrenimi görevi kullanıyorsa, ürün ekibine neden araştırır ve bulguları özellik geliştirme önceliğini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0768-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="b0768-109">ML.NET CLI telemetri Kilitlenmeler ve kod anormallikleri gibi sorunların hatalarını ayıklamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b0768-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="b0768-110">Ürün ekibine bu öngörüleri appreciates olsa da herkes bu verileri göndermek istiyor da biliyoruz.</span><span class="sxs-lookup"><span data-stu-id="b0768-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="b0768-111">Telemetri devre dışı bırakmak öğrenin.</span><span class="sxs-lookup"><span data-stu-id="b0768-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="b0768-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b0768-112">Scope</span></span>

<span data-ttu-id="b0768-113">`mlnet` ML.NET CLI komutu çalıştırır, ancak komut telemetri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="b0768-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="b0768-114">Telemetri *etkin değilse* çalıştırdığınızda `mlnet` bağlı herhangi bir komut ile komutu.</span><span class="sxs-lookup"><span data-stu-id="b0768-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="b0768-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0768-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="b0768-116">Telemetri *etkin* çalıştırdığınızda bir [ML.NET CLI komutunu](../reference/ml-net-cli-reference.md), gibi `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="b0768-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="b0768-117">Veri toplama işlemini iptal</span><span class="sxs-lookup"><span data-stu-id="b0768-117">Opt out of data collection</span></span>

<span data-ttu-id="b0768-118">ML.NET CLI telemetri özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="b0768-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="b0768-119">Ayarlayarak telemetri özelliği iyileştirilmiş `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.</span><span class="sxs-lookup"><span data-stu-id="b0768-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="b0768-120">Bu ortam değişkeni, genel .NET CLI aracı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b0768-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="b0768-121">Toplanan veri noktaları</span><span class="sxs-lookup"><span data-stu-id="b0768-121">Data points collected</span></span>

<span data-ttu-id="b0768-122">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="b0768-122">The feature collects the following data:</span></span>

- <span data-ttu-id="b0768-123">Hangi komut, gibi çağrıldı `auto-train`</span><span class="sxs-lookup"><span data-stu-id="b0768-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="b0768-124">Komut satırı parametresi adları kullanılır (yani "veri kümesi adı, etiket sütun adı, ml görev, çıkış yolu, araştırma zaman sınırı, ayrıntı düzeyi")</span><span class="sxs-lookup"><span data-stu-id="b0768-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="b0768-125">Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz bir kimliği bir makine için</span><span class="sxs-lookup"><span data-stu-id="b0768-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="b0768-126">Zaman damgası bir çağırma</span><span class="sxs-lookup"><span data-stu-id="b0768-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="b0768-127">Yalnızca coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresini (IP adresi değil tam)</span><span class="sxs-lookup"><span data-stu-id="b0768-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="b0768-128">Kullanılan tüm bağımsız değişkenler/parametreler adı.</span><span class="sxs-lookup"><span data-stu-id="b0768-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="b0768-129">Dizeleri gibi müşteri'nin değerlerini değil</span><span class="sxs-lookup"><span data-stu-id="b0768-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="b0768-130">Karma veri kümesi dosya adı</span><span class="sxs-lookup"><span data-stu-id="b0768-130">Hashed dataset filename</span></span>
- <span data-ttu-id="b0768-131">Veri kümesi dosyası boyut demetinde</span><span class="sxs-lookup"><span data-stu-id="b0768-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="b0768-132">İşletim sistemi ve sürümü</span><span class="sxs-lookup"><span data-stu-id="b0768-132">Operating system and version</span></span>
- <span data-ttu-id="b0768-133">--Görev parametresinin değeri: Gibi kategorik değerler `regression`, `binary-classification`, ve `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="b0768-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="b0768-134">ML.NET CLI sürümü (yani 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="b0768-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="b0768-135">Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) kısıtlı erişim'in altında tutulması ve katı güvenlik denetimleri güvenli altında kullanılan teknoloji [Azure depolama](https://azure.microsoft.com/services/storage/) sistemler.</span><span class="sxs-lookup"><span data-stu-id="b0768-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="b0768-136">Veri noktaları toplanmadı</span><span class="sxs-lookup"><span data-stu-id="b0768-136">Data points not collected</span></span>
<span data-ttu-id="b0768-137">Telemetri özellik *değil* toplayın:</span><span class="sxs-lookup"><span data-stu-id="b0768-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="b0768-138">kullanıcı adları gibi kişisel veriler</span><span class="sxs-lookup"><span data-stu-id="b0768-138">personal data, such as usernames</span></span>
- <span data-ttu-id="b0768-139">veri kümesi dosya adları</span><span class="sxs-lookup"><span data-stu-id="b0768-139">dataset filenames</span></span>
- <span data-ttu-id="b0768-140">veri kümesi dosyalardan alınan veriler</span><span class="sxs-lookup"><span data-stu-id="b0768-140">data from dataset files</span></span>

<span data-ttu-id="b0768-141">ML.NET CLI telemetri hassas veriler ya da toplama şüpheleniyorsanız veri endpoınt yapılıyor veya uygunsuz bir şekilde ele, sorunu bildirin [ML.NET](https://github.com/dotnet/machinelearning) araştırma için depo.</span><span class="sxs-lookup"><span data-stu-id="b0768-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="b0768-142">Lisans</span><span class="sxs-lookup"><span data-stu-id="b0768-142">License</span></span>

<span data-ttu-id="b0768-143">Microsoft Dağıtım ML.NET CLI ile lisanslı [Microsoft Yazılımı Lisans koşulları: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="b0768-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="b0768-144">Veri toplama ve işleme hakkında daha fazla bilgi için "Veri" başlıklı bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="b0768-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="b0768-145">Açığa çıkması</span><span class="sxs-lookup"><span data-stu-id="b0768-145">Disclosure</span></span>

<span data-ttu-id="b0768-146">İlk kez çalıştırdığınızda bir [ML.NET CLI komutunu](../reference/ml-net-cli-reference.md) gibi `mlnet auto-train`, ML.NET CLI araç telemetri dışında nasıl söyler açığa metin görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b0768-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="b0768-147">Metin, çalıştırmakta olduğunuz CLI sürümüne bağlı olarak biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="b0768-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0768-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0768-148">See also</span></span>
- [<span data-ttu-id="b0768-149">ML.NET CLI başvurusu</span><span class="sxs-lookup"><span data-stu-id="b0768-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b0768-150">Microsoft Yazılımı Lisans koşulları: Microsoft .NET kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b0768-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="b0768-151">Microsoft gizlilik</span><span class="sxs-lookup"><span data-stu-id="b0768-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="b0768-152">Microsoft gizlilik bildirimi</span><span class="sxs-lookup"><span data-stu-id="b0768-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
