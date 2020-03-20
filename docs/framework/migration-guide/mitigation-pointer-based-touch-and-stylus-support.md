---
title: 'Azaltma: Pointer tabanlı Dokunmatik ve Stylus Desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094481"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="a9c17-102">Azaltma: Pointer tabanlı Dokunmatik ve Stylus Desteği</span><span class="sxs-lookup"><span data-stu-id="a9c17-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="a9c17-103">.NET Framework 4.7'yi hedefleyen ve Windows 10 Creators Update'ten başlayarak `WM_POINTER`Windows'da çalışan WPF uygulamaları isteğe bağlı wpf dokunmatik/stylus yığınına olanak sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a9c17-103">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="a9c17-104">Etki</span><span class="sxs-lookup"><span data-stu-id="a9c17-104">Impact</span></span>

<span data-ttu-id="a9c17-105">İşaretçi tabanlı dokunma/kalem desteğini açıkça etkinleştirmeyen geliştiriciler, WPF touch/stylus davranışında herhangi bir değişiklik görmemelidir.</span><span class="sxs-lookup"><span data-stu-id="a9c17-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="a9c17-106">İsteğe bağlı `WM_POINTER`tabanlı dokunmatik/kalem yığınıyla ilgili bilinen güncel sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a9c17-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="a9c17-107">Gerçek zamanlı mürekkep için destek yok.</span><span class="sxs-lookup"><span data-stu-id="a9c17-107">No support for real-time inking.</span></span>

   <span data-ttu-id="a9c17-108">Mürekkep ve kalem eklentileri hala çalışırken, düşük performansa yol açabilecek ui iş parçacığı üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="a9c17-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="a9c17-109">Dokunma/kalem etkinliklerinden fare olaylarına terfi değişiklikleri nedeniyle davranış değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="a9c17-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="a9c17-110">Manipülasyon farklı davranabilir.</span><span class="sxs-lookup"><span data-stu-id="a9c17-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="a9c17-111">Sürükle/Bırak, dokunma girişi için uygun geri bildirim göstermez.</span><span class="sxs-lookup"><span data-stu-id="a9c17-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="a9c17-112">(Bu, kalem girişini etkilemez.)</span><span class="sxs-lookup"><span data-stu-id="a9c17-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="a9c17-113">Dokunma/kalem olaylarında Sürükle/Bırak başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="a9c17-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="a9c17-114">Bu, fare girişi algılanıncaya kadar uygulamanın yanıt vermemesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9c17-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="a9c17-115">Bunun yerine, geliştiriciler fare olaylarından sürükle ve bırak başlatmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9c17-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="a9c17-116">WM_POINTER tabanlı dokunmatik/stylus desteğini seçme</span><span class="sxs-lookup"><span data-stu-id="a9c17-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="a9c17-117">Bu yığını etkinleştirmek isteyen geliştiriciler, uygulamalarının *app.config* dosyasına aşağıdakileri ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a9c17-117">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="a9c17-118">Bu girişi kaldırmak veya bu `false` isteğe bağlı yığını kapatmak için değerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="a9c17-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9c17-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9c17-119">See also</span></span>

- [<span data-ttu-id="a9c17-120">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="a9c17-120">Application compatibility</span></span>](application-compatibility.md)
