---
title: 'Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094481"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="cfbc9-102">Risk azaltma: Işaretçi tabanlı dokunmatik ve Stilus desteği</span><span class="sxs-lookup"><span data-stu-id="cfbc9-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="cfbc9-103">.NET Framework 4,7 ' i hedefleyen ve Windows 10 Creators Update ile başlayan WPF uygulamaları, isteğe bağlı `WM_POINTER`tabanlı bir WPF dokunmatik/Stilus yığınını etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-103">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="cfbc9-104">Etkisi</span><span class="sxs-lookup"><span data-stu-id="cfbc9-104">Impact</span></span>

<span data-ttu-id="cfbc9-105">İşaretçi tabanlı dokunmatik/ekran kalemi desteğinin açıkça etkinleştirilmedikleri geliştiriciler WPF dokunma/ekran kalemi davranışında değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="cfbc9-106">Aşağıda, isteğe bağlı `WM_POINTER`tabanlı dokunmatik/ekran kalemi yığınında bilinen güncel sorunlar verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfbc9-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="cfbc9-107">Gerçek zamanlı mürekkep oluşturma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-107">No support for real-time inking.</span></span>

   <span data-ttu-id="cfbc9-108">Mürekkep oluşturma ve ekran kalemi eklentileri çalışmaya devam ederken, Kullanıcı arabirimi iş parçacığında işlenir ve bu da kötü performansa yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="cfbc9-109">Dokunmatik/ekran kalemi olaylarından fare olaylarına yükseltme yapılan değişiklikler nedeniyle davranış değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="cfbc9-110">Düzenleme farklı davranabilirler.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="cfbc9-111">Sürükle/bırak, dokunma girişi için uygun geri bildirimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="cfbc9-112">(Bu, Stilus girişini etkilemez.)</span><span class="sxs-lookup"><span data-stu-id="cfbc9-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="cfbc9-113">Sürükle/bırak, artık dokunmatik/ekran kalemi olaylarında başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="cfbc9-114">Bu, fare girişi algılanana kadar uygulamanın yanıt vermemesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="cfbc9-115">Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak işlemini başlatmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="cfbc9-116">WM_POINTER tabanlı dokunmatik/ekran kalemi desteğiyle opzip</span><span class="sxs-lookup"><span data-stu-id="cfbc9-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="cfbc9-117">Bu yığını etkinleştirmek isteyen geliştiriciler aşağıdakini uygulamanın *app. config* dosyasına ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-117">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="cfbc9-118">Bu girdiyi kaldırmak veya değerini `false` olarak ayarlamak, bu isteğe bağlı yığını kapatır.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfbc9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-119">See also</span></span>

- [<span data-ttu-id="cfbc9-120">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="cfbc9-120">Application compatibility</span></span>](application-compatibility.md)
