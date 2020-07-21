---
title: 'Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği'
description: .NET Framework 4,7 ' i hedefleyen WPF uygulamaları için isteğe bağlı WPF Touch/Stilus yığınını etkinleştirmenin etkileri hakkında bilgi edinin.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475430"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="874ea-103">Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği</span><span class="sxs-lookup"><span data-stu-id="874ea-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="874ea-104">.NET Framework 4,7 ' i hedefleyen ve Windows 10 Creators Update ile başlayarak Windows üzerinde çalışan WPF uygulamaları, isteğe bağlı tabanlı bir `WM_POINTER` WPF dokunmatik/Stilus yığınını etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="874ea-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="874ea-105">Etki</span><span class="sxs-lookup"><span data-stu-id="874ea-105">Impact</span></span>

<span data-ttu-id="874ea-106">İşaretçi tabanlı dokunmatik/ekran kalemi desteğinin açıkça etkinleştirilmedikleri geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="874ea-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="874ea-107">İsteğe bağlı `WM_POINTER` tabanlı dokunmatik/Stilus Stack ile ilgili olarak bilinen geçerli sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="874ea-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="874ea-108">Gerçek zamanlı mürekkep oluşturma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="874ea-108">No support for real-time inking.</span></span>

   <span data-ttu-id="874ea-109">Mürekkep oluşturma ve ekran kalemi eklentileri çalışmaya devam ederken, Kullanıcı arabirimi iş parçacığında işlenir ve bu da kötü performansa yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="874ea-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="874ea-110">Dokunmatik/ekran kalemi olaylarından fare olaylarına yükseltme yapılan değişiklikler nedeniyle davranış değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="874ea-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="874ea-111">Düzenleme farklı davranabilirler.</span><span class="sxs-lookup"><span data-stu-id="874ea-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="874ea-112">Sürükle/bırak, dokunma girişi için uygun geri bildirimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="874ea-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="874ea-113">(Bu, Stilus girişini etkilemez.)</span><span class="sxs-lookup"><span data-stu-id="874ea-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="874ea-114">Sürükle/bırak, artık dokunmatik/ekran kalemi olaylarında başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="874ea-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="874ea-115">Bu, fare girişi algılanana kadar uygulamanın yanıt vermemesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="874ea-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="874ea-116">Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak işlemini başlatmalıdır.</span><span class="sxs-lookup"><span data-stu-id="874ea-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="874ea-117">WM_POINTER tabanlı dokunmatik/ekran kalemi desteğiyle opzip</span><span class="sxs-lookup"><span data-stu-id="874ea-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="874ea-118">Bu yığını etkinleştirmek isteyen geliştiriciler aşağıdakini uygulamanın *app.config* dosyasına ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="874ea-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="874ea-119">Bu giriş kaldırılıyor veya değeri, `false` Bu isteğe bağlı yığını devre dışı olarak ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="874ea-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="874ea-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="874ea-120">See also</span></span>

- [<span data-ttu-id="874ea-121">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="874ea-121">Application compatibility</span></span>](application-compatibility.md)
