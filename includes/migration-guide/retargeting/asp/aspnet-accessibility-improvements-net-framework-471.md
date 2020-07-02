---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614679"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a><span data-ttu-id="fe69f-101">.NET Framework 4.7.1 'de erişilebilirlik Iyileştirmeleri ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fe69f-101">ASP.NET Accessibility Improvements in .NET Framework 4.7.1</span></span>

#### <a name="details"></a><span data-ttu-id="fe69f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fe69f-102">Details</span></span>

<span data-ttu-id="fe69f-103">4.7.1, ASP.NET .NET Framework ile başlayarak, ASP.NET müşterilerini daha iyi desteklemek için ASP.NET Web denetimlerinin Visual Studio 'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe69f-103">Starting with the .NET Framework 4.7.1, ASP.NET has improved how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="fe69f-104">Bunlar aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="fe69f-104">These include the following changes:</span></span>

- <span data-ttu-id="fe69f-105">Ayrıntılar görünümü sihirbazındaki alan Ekle iletişim kutusu ya da ListView sihirbazının ListView yapılandırma iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="fe69f-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard, or the Configure ListView dialog of the ListView wizard.</span></span>
- <span data-ttu-id="fe69f-106">Veri sayfalayıcı alanları Düzenleyicisi gibi Yüksek Karşıtlık modunda görüntüyü geliştirmek için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="fe69f-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span>
- <span data-ttu-id="fe69f-107">DataPager denetiminin sayfalayıcı alanlarını Düzenle Sihirbazı 'ndaki alanlar iletişim kutusu gibi denetimler için klavye gezinti deneyimlerini geliştirmek üzere yapılan değişiklikler veya veri kaynağını yapılandırma Sihirbazı 'nın veri kaynağını yapılandırma Sihirbazı ' nın veri seçimini Yapılandır iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="fe69f-107">Changes to improve the keyboard navigation experiences for controls, like the Fields dialog in the Edit Pager Fields wizard of the DataPager control, the Configure ObjectContext dialog, or the Configure Data Selection dialog of the Configure Data Source wizard.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe69f-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="fe69f-108">Suggestion</span></span>

<span data-ttu-id="fe69f-109">**Bu değişiklikleri kabul etme veya devre dışı bırakma** Visual Studio Tasarımcısı 'nın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.1 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe69f-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="fe69f-110">Web uygulaması aşağıdaki yollarla bu değişikliklerden faydalanabilir:</span><span class="sxs-lookup"><span data-stu-id="fe69f-110">The web application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="fe69f-111">Varsayılan olarak aşağıdaki AppContext anahtarıyla yeni erişilebilirlik özelliklerini destekleyen Visual Studio 2017 15,3 veya üstünü yükler.</span><span class="sxs-lookup"><span data-stu-id="fe69f-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span>
- <span data-ttu-id="fe69f-112">`Switch.UseLegacyAccessibilityFeatures` `<runtime>` `false` Aşağıdaki örnekte gösterildiği gibi, appcontext anahtarını devenv.exe.config dosyasında bölümüne ekleyerek ve olarak ayarlayarak eski erişilebilirlik davranışlarını geri çevirin.</span><span class="sxs-lookup"><span data-stu-id="fe69f-112">Opt out of the legacy accessibility behaviors by adding the `Switch.UseLegacyAccessibilityFeatures` AppContext switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

<span data-ttu-id="fe69f-113">.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .</span><span class="sxs-lookup"><span data-stu-id="fe69f-113">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="fe69f-114">Name</span><span class="sxs-lookup"><span data-stu-id="fe69f-114">Name</span></span>    | <span data-ttu-id="fe69f-115">Değer</span><span class="sxs-lookup"><span data-stu-id="fe69f-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fe69f-116">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fe69f-116">Scope</span></span>   | <span data-ttu-id="fe69f-117">İkincil</span><span class="sxs-lookup"><span data-stu-id="fe69f-117">Minor</span></span>       |
| <span data-ttu-id="fe69f-118">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fe69f-118">Version</span></span> | <span data-ttu-id="fe69f-119">4.7.1</span><span class="sxs-lookup"><span data-stu-id="fe69f-119">4.7.1</span></span>       |
| <span data-ttu-id="fe69f-120">Tür</span><span class="sxs-lookup"><span data-stu-id="fe69f-120">Type</span></span>    | <span data-ttu-id="fe69f-121">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="fe69f-121">Retargeting</span></span> |
