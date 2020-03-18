---
title: ML.NET CLI tarafından Telemetri koleksiyonu
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve nasıl devre dışı kalınan CLI telemetri özellikleri ML.NET hakkında bilgi edinin. Ayrıca, .NET lisans sözleşmesine bağlantılar ve Microsoft GDPR uyumluluğu hakkındaki bilgileri bulun.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849750"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="59db8-104">ML.NET CLI tarafından Telemetri koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="59db8-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="59db8-105">[CLI ML.NET,](https://aka.ms/mlnet-cli) Microsoft tarafından kullanılmak üzere toplanan anonim kullanım verilerini toplayan bir telemetri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="59db8-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="59db8-106">Microsoft verileri nasıl kullanır?</span><span class="sxs-lookup"><span data-stu-id="59db8-106">How Microsoft uses the data</span></span>

<span data-ttu-id="59db8-107">Ürün ekibi, araçları nasıl geliştireceğini anlamama yardımcı olmak için ML.NET CLI telemetri verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="59db8-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="59db8-108">Örneğin, müşteriler belirli bir makine öğrenimi görevini seyrek olarak kullanıyorsa, ürün ekibi neden olduğunu araştırır ve özellik geliştirmeye öncelik vermek için bulguları kullanır.</span><span class="sxs-lookup"><span data-stu-id="59db8-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="59db8-109">ML.NET CLI telemetri de çöker ve kod anomalileri gibi sorunların hata ayıklama ile yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="59db8-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span>

<span data-ttu-id="59db8-110">Ürün ekibi bu öngörüyü takdir etse de, herkesin bu verileri göndermek istemediğini de biliyoruz.</span><span class="sxs-lookup"><span data-stu-id="59db8-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="59db8-111">Telemetriyi nasıl devre dışı dışı katabileceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="59db8-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="59db8-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="59db8-112">Scope</span></span>

<span data-ttu-id="59db8-113">Komut `mlnet` CLI ML.NET başlatıyor, ancak komutun kendisi telemetri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="59db8-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="59db8-114">`mlnet` Komutu başka bir komut eklenmeden çalıştırdığınızda telemetri *etkinleştirilmez.*</span><span class="sxs-lookup"><span data-stu-id="59db8-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="59db8-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="59db8-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="59db8-116">Telemetri, [cli komutu gibi bir](../reference/ml-net-cli-reference.md)ML.NET `mlnet auto-train`çalıştırdığınızda *etkinleştirilir.*</span><span class="sxs-lookup"><span data-stu-id="59db8-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="59db8-117">Veri toplamayı devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="59db8-117">Opt out of data collection</span></span>

<span data-ttu-id="59db8-118">cli telemetri özelliğiML.NET varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="59db8-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="59db8-119">Ortam değişkenini `MLDOTNET_CLI_TELEMETRY_OPTOUT` `1` `true`ayarlayarak telemetri özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="59db8-119">Opt out of the telemetry feature by setting the `MLDOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="59db8-120">Bu ortam değişkeni, ML.NET CLI aracı için genel olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="59db8-120">This environment variable applies globally to the ML.NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="59db8-121">Toplanan veri noktaları</span><span class="sxs-lookup"><span data-stu-id="59db8-121">Data points collected</span></span>

<span data-ttu-id="59db8-122">Özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="59db8-122">The feature collects the following data:</span></span>

- <span data-ttu-id="59db8-123">Hangi komut çağrıldı, örneğin`auto-train`</span><span class="sxs-lookup"><span data-stu-id="59db8-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="59db8-124">Kullanılan komut satırı parametre adları (diğer bir şey, "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span><span class="sxs-lookup"><span data-stu-id="59db8-124">Command-line parameter names used (that is, "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="59db8-125">Hashed MAC adresi: bir makine için şifreleme (SHA256) anonim ve benzersiz bir kimlik</span><span class="sxs-lookup"><span data-stu-id="59db8-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="59db8-126">Bir çağırmanın zaman damgası</span><span class="sxs-lookup"><span data-stu-id="59db8-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="59db8-127">Yalnızca coğrafi konumu belirlemek için kullanılan üç sekizli IP adresi (tam IP adresi değil)</span><span class="sxs-lookup"><span data-stu-id="59db8-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="59db8-128">Kullanılan tüm bağımsız değişkenlerin/parametrelerin adı.</span><span class="sxs-lookup"><span data-stu-id="59db8-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="59db8-129">Dizeleri gibi müşterinin değerleri değil</span><span class="sxs-lookup"><span data-stu-id="59db8-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="59db8-130">Hashed dataset dosya adı</span><span class="sxs-lookup"><span data-stu-id="59db8-130">Hashed dataset filename</span></span>
- <span data-ttu-id="59db8-131">Dataset dosya boyutunda kova</span><span class="sxs-lookup"><span data-stu-id="59db8-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="59db8-132">İşletim sistemi ve sürüm</span><span class="sxs-lookup"><span data-stu-id="59db8-132">Operating system and version</span></span>
- <span data-ttu-id="59db8-133">--görev parametresi değeri: `regression`Kategorik değerler, `binary-classification`, , ve`multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="59db8-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="59db8-134">ML.NET CLI sürümü (yani, 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="59db8-134">ML.NET CLI version (that is, 0.3.27703.4)</span></span>

<span data-ttu-id="59db8-135">Veriler, sınırlı erişim altında tutulan ve güvenli [Azure Depolama](https://azure.microsoft.com/services/storage/) sistemlerinden gelen sıkı güvenlik denetimleri altında kullanılan [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) teknolojisini kullanarak Microsoft sunucularına güvenli bir şekilde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="59db8-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="59db8-136">Toplanmayan veri noktaları</span><span class="sxs-lookup"><span data-stu-id="59db8-136">Data points not collected</span></span>

<span data-ttu-id="59db8-137">Telemetri özelliği şunları *toplamaz:*</span><span class="sxs-lookup"><span data-stu-id="59db8-137">The telemetry feature *doesn't* collect:</span></span>

- <span data-ttu-id="59db8-138">kullanıcı adları gibi kişisel veriler</span><span class="sxs-lookup"><span data-stu-id="59db8-138">personal data, such as usernames</span></span>
- <span data-ttu-id="59db8-139">dataset dosya adları</span><span class="sxs-lookup"><span data-stu-id="59db8-139">dataset filenames</span></span>
- <span data-ttu-id="59db8-140">dataset dosyalarından gelen veriler</span><span class="sxs-lookup"><span data-stu-id="59db8-140">data from dataset files</span></span>

<span data-ttu-id="59db8-141">CLI telemetrisinin ML.NET hassas verileri topladığından veya verilerin güvensiz veya uygunsuz şekilde işlendiğini sanıyorsanız, ML.NET [deposunda](https://github.com/dotnet/machinelearning) bir sorun dosyalayarak inceleme için bir sorun bulun.</span><span class="sxs-lookup"><span data-stu-id="59db8-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="59db8-142">Lisans</span><span class="sxs-lookup"><span data-stu-id="59db8-142">License</span></span>

<span data-ttu-id="59db8-143">CLI'ML.NET Microsoft dağıtımı Microsoft Yazılım Lisans Koşulları ile [lisanslanmıştır: Microsoft .NET Kitaplığı.](https://aka.ms/dotnet-core-eula)</span><span class="sxs-lookup"><span data-stu-id="59db8-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="59db8-144">Veri toplama ve işleme ile ilgili ayrıntılar için "Veri" başlıklı bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="59db8-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="59db8-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59db8-145">Disclosure</span></span>

<span data-ttu-id="59db8-146">CLI ML.NET aracı gibi `mlnet auto-train`bir ML.NET [CLI komutunu](../reference/ml-net-cli-reference.md) ilk çalıştırdığınızda, telemetriyi nasıl devre dışı bırakmanız gerektiğini belirten açıklama metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59db8-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="59db8-147">Metin, çalıştırdığınız CLI sürümüne bağlı olarak biraz değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="59db8-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="59db8-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59db8-148">See also</span></span>

- [<span data-ttu-id="59db8-149">ML.NET CLI başvurusu</span><span class="sxs-lookup"><span data-stu-id="59db8-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="59db8-150">Microsoft Yazılım Lisans Koşulları: Microsoft .NET Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="59db8-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="59db8-151">Microsoft'ta gizlilik</span><span class="sxs-lookup"><span data-stu-id="59db8-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="59db8-152">Microsoft Gizlilik Bildirimi</span><span class="sxs-lookup"><span data-stu-id="59db8-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
