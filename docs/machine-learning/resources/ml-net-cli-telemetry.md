---
title: ML.NET CLı tarafından telemetri toplama
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve devre dışı bırakılacağı ML.NET CLı telemetri özellikleri hakkında bilgi edinin. Ayrıca, .NET lisans sözleşmesinin bağlantılarını ve Microsoft GDPR uyumluluğu hakkındaki bilgileri bulabilirsiniz.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: eab1e37d7d0d47251c4f92422730b105cf2db265
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433787"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="704c0-104">ML.NET CLı tarafından telemetri toplama</span><span class="sxs-lookup"><span data-stu-id="704c0-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="704c0-105">[Ml.net CLI](https://aka.ms/mlnet-cli) , Microsoft tarafından kullanılmak üzere toplanan anonim kullanım verilerini toplayan bir telemetri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="704c0-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="704c0-106">Microsoft verileri nasıl kullanır?</span><span class="sxs-lookup"><span data-stu-id="704c0-106">How Microsoft uses the data</span></span>

<span data-ttu-id="704c0-107">Ürün ekibi, araçların nasıl geliştirilmesine yardımcı olmak için ML.NET CLı telemetri verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="704c0-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="704c0-108">Örneğin, müşteriler belirli bir makine öğrenimi görevini sık sık kullanıyorsa, ürün ekibi, özellik geliştirmeyi önceliklendirmek için neden ve bulguları araştırır kullanır.</span><span class="sxs-lookup"><span data-stu-id="704c0-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="704c0-109">ML.NET CLı telemetrisi, çökmeler ve kod bozuklukları gibi sorunların hatalarını ayıklamanıza de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="704c0-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="704c0-110">Ürün ekibi bu öngörüleri öğrenirken, herkesin bu verileri göndermek istediğini da biliyoruz.</span><span class="sxs-lookup"><span data-stu-id="704c0-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="704c0-111">Telemetriyi devre dışı bırakmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="704c0-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="704c0-112">`Scope`</span><span class="sxs-lookup"><span data-stu-id="704c0-112">Scope</span></span>

<span data-ttu-id="704c0-113">`mlnet` Komut ml.net CLI 'yi başlatır, ancak komut telemetri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="704c0-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="704c0-114">`mlnet` Komutu başka bir komut ekli olmadan çalıştırdığınızda telemetri *etkin değildir* .</span><span class="sxs-lookup"><span data-stu-id="704c0-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="704c0-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="704c0-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="704c0-116">Telemetri`mlnet auto-train`, gıbı bir [ml.net CLI komutu](../reference/ml-net-cli-reference.md)çalıştırdığınızda *etkinleştirilir* .</span><span class="sxs-lookup"><span data-stu-id="704c0-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="704c0-117">Veri toplamayı geri çevirme</span><span class="sxs-lookup"><span data-stu-id="704c0-117">Opt out of data collection</span></span>

<span data-ttu-id="704c0-118">ML.NET CLı telemetri özelliği varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="704c0-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="704c0-119">`DOTNET_CLI_TELEMETRY_OPTOUT` Ortam değişkenini `1` veya`true`olarak ayarlayarak telemetri özelliğini geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="704c0-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="704c0-120">Bu ortam değişkeni, .NET CLı aracı için global olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="704c0-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="704c0-121">Toplanan veri noktaları</span><span class="sxs-lookup"><span data-stu-id="704c0-121">Data points collected</span></span>

<span data-ttu-id="704c0-122">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="704c0-122">The feature collects the following data:</span></span>

- <span data-ttu-id="704c0-123">Çağrılan komut`auto-train`</span><span class="sxs-lookup"><span data-stu-id="704c0-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="704c0-124">Kullanılan komut satırı parametre adları (örneğin, "DataSet-Name, Label-Column-Name, ml-Task, Output-Path, Max-araştırma zamanı, ayrıntı")</span><span class="sxs-lookup"><span data-stu-id="704c0-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="704c0-125">Karma hale getirilmiş MAC adresi: bir makine için bir şifreleme (SHA256) anonim ve benzersiz KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="704c0-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="704c0-126">Bir çağrının zaman damgası</span><span class="sxs-lookup"><span data-stu-id="704c0-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="704c0-127">Yalnızca coğrafi konumu belirlemede kullanılan üç sekizli IP adresi (tam IP adresi değil)</span><span class="sxs-lookup"><span data-stu-id="704c0-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="704c0-128">Kullanılan tüm bağımsız değişkenlerin/parametrelerin adı.</span><span class="sxs-lookup"><span data-stu-id="704c0-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="704c0-129">Müşterinin değerleri değil (dizeler gibi)</span><span class="sxs-lookup"><span data-stu-id="704c0-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="704c0-130">Karma veri kümesi dosya adı</span><span class="sxs-lookup"><span data-stu-id="704c0-130">Hashed dataset filename</span></span>
- <span data-ttu-id="704c0-131">Veri kümesi dosya boyutu demeti</span><span class="sxs-lookup"><span data-stu-id="704c0-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="704c0-132">İşletim sistemi ve sürümü</span><span class="sxs-lookup"><span data-stu-id="704c0-132">Operating system and version</span></span>
- <span data-ttu-id="704c0-133">--Görev parametresi değeri: , Ve gibi kategorik değerler `regression` `binary-classification``multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="704c0-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="704c0-134">ML.NET CLı sürümü (ör. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="704c0-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="704c0-135">Veriler, [azure Application Insights](https://azure.microsoft.com/services/application-insights/) teknolojisi kullanılarak Microsoft sunucularına güvenli bir şekilde gönderilir, kısıtlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="704c0-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="704c0-136">Veri noktaları toplanmadı</span><span class="sxs-lookup"><span data-stu-id="704c0-136">Data points not collected</span></span>
<span data-ttu-id="704c0-137">Telemetri *özelliği toplanmaz* :</span><span class="sxs-lookup"><span data-stu-id="704c0-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="704c0-138">Kullanıcı adları gibi kişisel veriler</span><span class="sxs-lookup"><span data-stu-id="704c0-138">personal data, such as usernames</span></span>
- <span data-ttu-id="704c0-139">veri kümesi dosya adları</span><span class="sxs-lookup"><span data-stu-id="704c0-139">dataset filenames</span></span>
- <span data-ttu-id="704c0-140">veri kümesi dosyalarından veriler</span><span class="sxs-lookup"><span data-stu-id="704c0-140">data from dataset files</span></span>

<span data-ttu-id="704c0-141">ML.NET CLı telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu kuşkulanıyorsanız, araştırma için [ml.net](https://github.com/dotnet/machinelearning) deposunda bir sorun verin.</span><span class="sxs-lookup"><span data-stu-id="704c0-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="704c0-142">Lisans</span><span class="sxs-lookup"><span data-stu-id="704c0-142">License</span></span>

<span data-ttu-id="704c0-143">ML.net CLI 'nin Microsoft dağıtımı, [Microsoft yazılımı lisans koşulları ile lisanslanır: Microsoft .NET kitaplığı](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="704c0-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="704c0-144">Veri toplama ve işleme hakkında daha fazla bilgi için "veri" başlıklı bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="704c0-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="704c0-145">Savunmasız</span><span class="sxs-lookup"><span data-stu-id="704c0-145">Disclosure</span></span>

<span data-ttu-id="704c0-146">Gibi bir [ml.net CLI komutunu](../reference/ml-net-cli-reference.md) `mlnet auto-train`ilk kez çalıştırdığınızda, ml.net CLI aracı Telemetriyi nasıl kabul eteceklerini belirten açıklama metnini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="704c0-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="704c0-147">Metin, çalıştırdığınız CLı sürümüne bağlı olarak biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="704c0-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="704c0-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="704c0-148">See also</span></span>
- [<span data-ttu-id="704c0-149">ML.NET CLı başvurusu</span><span class="sxs-lookup"><span data-stu-id="704c0-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="704c0-150">Microsoft yazılımı lisans koşulları: Microsoft .NET kitaplığı</span><span class="sxs-lookup"><span data-stu-id="704c0-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="704c0-151">Microsoft 'ta Gizlilik</span><span class="sxs-lookup"><span data-stu-id="704c0-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="704c0-152">Microsoft gizlilik bildirimi</span><span class="sxs-lookup"><span data-stu-id="704c0-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
