---
title: "Azaltma: İşaretçi tabanlı dokunma ve Kalem desteği"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
caps.latest.revision: "2"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78a7365d9bc82111ebd27f40e999c24d8f9ebfde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="7d95c-102">Azaltma: İşaretçi tabanlı dokunma ve Kalem desteği</span><span class="sxs-lookup"><span data-stu-id="7d95c-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="7d95c-103">.NET Framework 4.7 hedefleyen ve Windows 10 oluşturucuları güncelleştirmesi ile başlayarak Windows sistemlerinde çalışan WPF uygulamaları isteğe bağlı bir etkinleştirebilir `WM_POINTER`-WPF dokunma/kalem yığın tabanlı.</span><span class="sxs-lookup"><span data-stu-id="7d95c-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="7d95c-104">Etki</span><span class="sxs-lookup"><span data-stu-id="7d95c-104">Impact</span></span>

<span data-ttu-id="7d95c-105">İşaretçi tabanlı dokunma/kalem desteğini açıkça etkinleştirmeyin geliştiriciler WPF dokunma/kalem davranışında değişiklik görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d95c-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="7d95c-106">Aşağıdaki bilinen geçerli sorunlar isteğe bağlı olan `WM_POINTER`-touch/kalem yığın tabanlı:</span><span class="sxs-lookup"><span data-stu-id="7d95c-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="7d95c-107">Gerçek zamanlı mürekkep desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="7d95c-107">No support for real-time inking.</span></span>

   <span data-ttu-id="7d95c-108">Mürekkep ve Kalem eklentileri çalışmaya devam ederken, düşük performans açabilir kullanıcı Arabirimi iş parçacığı üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="7d95c-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="7d95c-109">Davranış değişiklikleri fare olayları dokunma/kalem olaylardan yükseltmesine değişiklikleri nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="7d95c-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="7d95c-110">İşleme farklı davranabilir.</span><span class="sxs-lookup"><span data-stu-id="7d95c-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="7d95c-111">Sürükle ve bırak dokunma girişi için uygun bildirim göstermez.</span><span class="sxs-lookup"><span data-stu-id="7d95c-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="7d95c-112">(Bu kalem giriş etkilemez.)</span><span class="sxs-lookup"><span data-stu-id="7d95c-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="7d95c-113">Sürükle ve bırak artık dokunma/kalem olaylarına başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d95c-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="7d95c-114">Fare girişi algılandığında kadar bu uygulama potansiyel olarak askıda kalabilir.</span><span class="sxs-lookup"><span data-stu-id="7d95c-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="7d95c-115">Bunun yerine, geliştiricilerin Sürükle başlatmak ve bu fare olayları bırakma gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d95c-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="7d95c-116">Dokunma/kalem WM_POINTER tabanlı desteklemek için seçim</span><span class="sxs-lookup"><span data-stu-id="7d95c-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="7d95c-117">Bu yığın etkinleştirmek istediğiniz geliştiriciler, uygulamanın app.config dosyasına aşağıdaki ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d95c-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="7d95c-118">Bu girdi kaldırma veya değeri ayarını `false` Bu isteğe bağlı yığını kapatır.</span><span class="sxs-lookup"><span data-stu-id="7d95c-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d95c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d95c-119">See also</span></span>

[<span data-ttu-id="7d95c-120">.NET Framework 4.7 yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7d95c-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
