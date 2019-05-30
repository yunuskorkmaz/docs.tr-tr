---
title: 'Azaltma: İşaretçi tabanlı dokunmatik ve Kalem desteği'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9264d8eb7923663061f9bccfffe5b8f5254549f0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379895"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="7b3d6-102">Azaltma: İşaretçi tabanlı dokunmatik ve Kalem desteği</span><span class="sxs-lookup"><span data-stu-id="7b3d6-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="7b3d6-103">.NET Framework 4.7 hedefleyen ve Windows 10 Creators güncelleştirmesi ile başlayarak Windows sistemleri üzerinde çalışan WPF uygulamalarını isteğe bağlı olarak etkinleştirebilir `WM_POINTER`-WPF dokunma/ekran kalemi yığın tabanlı.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="7b3d6-104">Etki</span><span class="sxs-lookup"><span data-stu-id="7b3d6-104">Impact</span></span>

<span data-ttu-id="7b3d6-105">Geliştiriciler, işaretçi temelli dokunma/kalemi destek açıkça etkinleştirmeyin WPF dokunma/ekran kalemi davranışında değişiklik görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="7b3d6-106">İsteğe bağlı bilinen geçerli sorunlar aşağıda verilmiştir `WM_POINTER`-dokunma/ekran kalemi yığın tabanlı:</span><span class="sxs-lookup"><span data-stu-id="7b3d6-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="7b3d6-107">Gerçek zamanlı mürekkep desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-107">No support for real-time inking.</span></span>

   <span data-ttu-id="7b3d6-108">Mürekkep ve ekran kalemi eklenti hala çalışırken, düşük performansa neden olabilecek UI iş parçacığı üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="7b3d6-109">Davranış değişiklikleri nedeniyle değişiklikler, dokunma/ekran kalemi olaylardan yükseltmede fare olayları.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="7b3d6-110">İşleme farklı şekilde davranabilir.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="7b3d6-111">Sürükle ve bırak, dokunma girişini ilgili geri bildirim göstermez.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="7b3d6-112">(Bu iğne girişi etkilemez.)</span><span class="sxs-lookup"><span data-stu-id="7b3d6-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="7b3d6-113">Sürükle ve bırak, dokunma/ekran kalemi olayları artık başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="7b3d6-114">Bu durum uygulama fare girişi algılandığında kadar yanıt veremez duruma gelmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="7b3d6-115">Bunun yerine, geliştiriciler, sürükle başlatmak ve fare olayları bırakın.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="7b3d6-116">Dokunma/kalemi WM_POINTER tabanlı desteklemek için seçim</span><span class="sxs-lookup"><span data-stu-id="7b3d6-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="7b3d6-117">Bu yığın etkinleştirmek isteyen geliştiricilerin aşağıdakileri, uygulamanın app.config dosyasına ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7b3d6-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="7b3d6-118">Bu girişi kaldırılıyor veya ve değerini `false` isteğe bağlı Bu yığın kapatır.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b3d6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b3d6-119">See also</span></span>

- [<span data-ttu-id="7b3d6-120">.NET Framework 4.7 yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7b3d6-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
