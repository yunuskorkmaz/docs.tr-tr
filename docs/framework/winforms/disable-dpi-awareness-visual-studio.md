---
title: Visual Studio'da DPI tanıma devre dışı bırak
description: Windows Form Tasarımcısı HDPI monitörlerde Visual Studio, DPI kullanmayan bir işlem olarak çalıştırmayı öğrenin ve sınırlamalar açıklanır.
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65c997e12aa033b3b08d32c8ab76372e3c52a803
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935619"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="e1b31-103">Visual Studio'da DPI tanıma devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="e1b31-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="e1b31-104">Visual Studio otomatik olarak görünen ölçekler anlamına gelir inç (DPI) kullanan uygulama başına bir nokta var.</span><span class="sxs-lookup"><span data-stu-id="e1b31-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="e1b31-105">Uygulamanın DPI kullanan geçersiz olduğunu belirtiyor, işletim sistemi uygulamayı bir bit eşlem olarak ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="e1b31-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="e1b31-106">Bu davranış, DPI sanallaştırma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e1b31-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="e1b31-107">Uygulamayı hala % 100 ölçeklendirme veya 96 DPI çalışır olduğunu düşünüyor.</span><span class="sxs-lookup"><span data-stu-id="e1b31-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="e1b31-108">HDPI monitörde Windows Form Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="e1b31-108">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="e1b31-109">**Windows Form Tasarımcısı** ölçeklendirme desteği, Visual Studio'da yok.</span><span class="sxs-lookup"><span data-stu-id="e1b31-109">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="e1b31-110">Bazı formlarında açtığınızda bu görüntü sorunları neden **Windows Form Tasarımcısı** üzerinde yüksek nokta / inç (HDPI) izleyiciler.</span><span class="sxs-lookup"><span data-stu-id="e1b31-110">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="e1b31-111">Örnekler için aşağıdaki görüntüde gösterildiği gibi çakıştırmayı denetimleri görünebilir:</span><span class="sxs-lookup"><span data-stu-id="e1b31-111">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Windows Form Tasarımcısı HDPI İzleyicisi](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="e1b31-113">Visual Studio 2017 sürüm 15,8 ve daha sonra bir formda açtığınızda **Windows Form Tasarımcısı** HDPI izleyicide bir Visual Studio Tasarımcı üst kısmında sarı bir bilgi çubuğu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="e1b31-113">In Visual Studio 2017 version 15.8 and later, when you open a form in the **Windows Forms Designer** on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![DPI uyumlu modda yeniden Visual Studio'da bilgi çubuğu](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="e1b31-115">İletiyi okur **ölçeklendirme, ana görüntü %200 (192 dpi) ayarlayın. Bu, Tasarımcı penceresinin içinde işleme sorunlara neden olabilir.**</span><span class="sxs-lookup"><span data-stu-id="e1b31-115">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

<span data-ttu-id="e1b31-116">Tasarımcıda çalışmayan ve formunuzu düzenleme gerekmez bilgi çubuğu yoksay ve Kod Düzenleyicisi'ni veya diğer türde tasarımcıları çalışma devam edin.</span><span class="sxs-lookup"><span data-stu-id="e1b31-116">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="e1b31-117">Yalnızca **Windows Form Tasarımcısı** etkilenir.</span><span class="sxs-lookup"><span data-stu-id="e1b31-117">Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="e1b31-118">Çalışmak ihtiyacınız varsa **Windows Form Tasarımcısı**, sonraki bölümde yardımcı [sorununu](#to-resolve-the-problem).</span><span class="sxs-lookup"><span data-stu-id="e1b31-118">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-problem).</span></span>

## <a name="to-resolve-the-problem"></a><span data-ttu-id="e1b31-119">Bu sorunu gidermek için</span><span class="sxs-lookup"><span data-stu-id="e1b31-119">To resolve the problem</span></span>

<span data-ttu-id="e1b31-120">Görünen bu sorunu gidermek için kullanabileceğiniz üç seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="e1b31-120">There are three options to resolve the display problem.</span></span>

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="e1b31-121">DPI kullanmayan bir işlem olarak Visual Studio'yu yeniden başlatın</span><span class="sxs-lookup"><span data-stu-id="e1b31-121">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="e1b31-122">Sarı bilgi çubuğunda seçeneğini belirleyerek, DPI kullanmayan bir işlem olarak Visual Studio yeniden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b31-122">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="e1b31-123">Bu sorunu çözümleme tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="e1b31-123">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="e1b31-124">Visual Studio, DPI kullanmayan bir işlem olarak çalıştığında, Tasarımcı düzen sorunları çözümlendi ancak yazı tipleri bulanık görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b31-124">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="e1b31-125">Visual Studio bildiren DPI kullanmayan bir işlem olarak çalışır, farklı bir sarı bilgilendirme iletisi görüntüler **Visual Studio, DPI kullanmayan bir işlem olarak çalışıyor. WPF ve XAML tasarımcıları düzgün görüntülenmeyebilir.**</span><span class="sxs-lookup"><span data-stu-id="e1b31-125">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="e1b31-126">Bilgi çubuğu için bir seçenek de sağlar. **DPI kullanan bir işlem olarak Visual Studio'yu yeniden başlatın**.</span><span class="sxs-lookup"><span data-stu-id="e1b31-126">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="e1b31-127">Bu araç pencereleri konumunu, DPI kullanmayan bir işlem olarak yeniden başlatma seçeneğini seçtiğinizde Visual Studio araç pencerelerinde akıyor, değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b31-127">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="e1b31-128">Varsayılan Visual Basic profil kullanıyorsanız veya varsa **oluşturulduğunda yeni projeleri Kaydet** seçeneği seçili olarak **Araçları** > **seçenekleri**  >  **Projeler ve çözümler**, DPI kullanmayan bir işlem olarak yeniden başlatıldığında, Visual Studio projenizi yeniden açamıyor.</span><span class="sxs-lookup"><span data-stu-id="e1b31-128">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="e1b31-129">Ancak, proje altında seçerek açabileceğiniz **dosya** > **son projeler ve çözümler**.</span><span class="sxs-lookup"><span data-stu-id="e1b31-129">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="e1b31-130">İşiniz bittiğinde çalışan DPI kullanan bir işlem olarak Visual Studio'yu yeniden önemlidir **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="e1b31-130">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="e1b31-131">DPI kullanmayan bir işlem olarak çalıştırılırken, yazı tipleri konum bulanık ve diğer tasarımcılar sorunları gibi görebilirsiniz **XAML Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="e1b31-131">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="e1b31-132">Kapatıp DPI uyumlu modda çalışırken Visual Studio, bu duruma DPI kullanan yeniden.</span><span class="sxs-lookup"><span data-stu-id="e1b31-132">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="e1b31-133">Ayrıca **DPI kullanan bir işlem olarak Visual Studio'yu yeniden başlatın** bilgi çubuğunda seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e1b31-133">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="e1b31-134">Bir kayıt defteri girdisini ekleyin</span><span class="sxs-lookup"><span data-stu-id="e1b31-134">Add a registry entry</span></span>

<span data-ttu-id="e1b31-135">Kayıt defteri değişikliği yaparak Visual Studio DPI uyumlu işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b31-135">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="e1b31-136">Açık **Kayıt Defteri Düzenleyicisi'ni** ve bir girdiyi **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** alt anahtarı:</span><span class="sxs-lookup"><span data-stu-id="e1b31-136">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="e1b31-137">**Giriş**: % ProgramFiles (x86) %\Microsoft Visual Studio\2017\your-edition\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="e1b31-137">**Entry**: %ProgramFiles(x86)%\Microsoft Visual Studio\2017\your-edition\Common7\IDE\devenv.exe</span></span>

<span data-ttu-id="e1b31-138">**Tür**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="e1b31-138">**Type**: REG_SZ</span></span>

<span data-ttu-id="e1b31-139">**Değer**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="e1b31-139">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="e1b31-140">Kayıt defteri girişini kaldırın kadar visual Studio, DPI kullanmayan modda kalır.</span><span class="sxs-lookup"><span data-stu-id="e1b31-140">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="e1b31-141">Ekranınıza ayarı % 100 ölçeklendirme ayarlayın</span><span class="sxs-lookup"><span data-stu-id="e1b31-141">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="e1b31-142">Windows 10'da ayarı % 100 ölçeklendirme ekranınıza ayarlamak için şunu yazın **görüntü ayarlarını** görev çubuğunda arama kutusuna tıklayın ve ardından **görünüm ayarlarını değiştirme**.</span><span class="sxs-lookup"><span data-stu-id="e1b31-142">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="e1b31-143">İçinde **ayarları** penceresinde **metin, uygulamaları ve diğer öğelerin boyutunu değiştirme** için **% 100**.</span><span class="sxs-lookup"><span data-stu-id="e1b31-143">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="e1b31-144">Kullanıcı arabiriminin kullanılabilmesi için çok küçük zorlaştırabilir çünkü ayarı % 100'e ölçeklendirmeyi ekranınıza istenmeyen, olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1b31-144">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1b31-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b31-145">See also</span></span>

- [<span data-ttu-id="e1b31-146">Windows Forms'ta otomatik ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="e1b31-146">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)