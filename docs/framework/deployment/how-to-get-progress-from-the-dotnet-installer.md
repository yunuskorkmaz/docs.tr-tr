---
title: 'Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma'
description: .NET 4,5 Yükleyicisinden nasıl ilerleme alabileceğinizi öğrenin. Bu .NET sürümü için uygulamalar geliştirirseniz uygulamanızın kurulumuna .NET 4,5 kurulumunu dahil edebilirsiniz.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: 501fcaa7636d586ddfff8606768d4639fdc010d7
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904266"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="cbc23-104">Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="cbc23-104">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="cbc23-105">.NET Framework 4,5 yeniden dağıtılabilir bir çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="cbc23-105">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="cbc23-106">.NET Framework bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun önkoşul bir parçası olarak, (zincir) .NET Framework 4,5 kurulumunu dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-106">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="cbc23-107">Özelleştirilmiş veya Birleşik bir kurulum deneyimi sunmak için, .NET Framework 4,5 kurulumunu sessizce başlatmak ve uygulamanızın kurulum ilerlemesini gösterirken ilerlemesini izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-107">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="cbc23-108">Sessiz izlemeyi etkinleştirmek için, .NET Framework 4,5 kurulumu (izlenen), kurulumla iletişim kurmak için bellek eşlemeli g/ç (MıO) kesimini kullanarak bir protokolü tanımlar (izleyici veya bağlayıcı).</span><span class="sxs-lookup"><span data-stu-id="cbc23-108">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="cbc23-109">Bu protokol, bir Chainer 'ın ilerleme bilgilerini elde etme, ayrıntılı sonuçlar alma, iletilere yanıt verme ve .NET Framework 4,5 kurulumunu iptal etme yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbc23-109">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="cbc23-110">**Çağırma**.</span><span class="sxs-lookup"><span data-stu-id="cbc23-110">**Invocation**.</span></span> <span data-ttu-id="cbc23-111">.NET Framework 4,5 kurulumunu çağırmak ve MıO bölümünden ilerleme bilgileri almak için kurulum programınızın aşağıdakileri yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="cbc23-111">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="cbc23-112">.NET Framework 4,5 yeniden dağıtılabilir programını çağırın:</span><span class="sxs-lookup"><span data-stu-id="cbc23-112">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="cbc23-113">Burada *bölüm adı* uygulamanızı tanımlamak için kullanmak istediğiniz addır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-113">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="cbc23-114">.NET Framework kurulum, MıO bölümünü zaman uyumsuz olarak okur ve yazar, bu nedenle bu süre içinde olayları ve iletileri kullanmayı kullanışlı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-114">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="cbc23-115">Örnekte, .NET Framework kurulum işlemi her ikisi de MıO bölümünü ( `TheSectionName` ) ayıran ve bir olayı () tanımlayan bir Oluşturucu tarafından oluşturulur `TheEventName` :</span><span class="sxs-lookup"><span data-stu-id="cbc23-115">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="cbc23-116">Lütfen bu adları kurulum programınızın benzersiz adlarıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cbc23-116">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="cbc23-117">MıO bölümünden okuyun.</span><span class="sxs-lookup"><span data-stu-id="cbc23-117">Read from the MMIO section.</span></span> <span data-ttu-id="cbc23-118">.NET Framework 4,5 ' de, indirme ve yükleme işlemleri eşzamanlı olarak bulunur: başka bir bölüm indirilirken .NET Framework bir parçası yükleniyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-118">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="cbc23-119">Sonuç olarak, devam eden ( `m_downloadSoFar` ve `m_installSoFar` ) 0 ile 255 arasında bir artış olan MIO bölümüne geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-119">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="cbc23-120">255 yazıldığında ve .NET Framework çıktığında yükleme tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-120">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="cbc23-121">**Çıkış kodları**.</span><span class="sxs-lookup"><span data-stu-id="cbc23-121">**Exit codes**.</span></span> <span data-ttu-id="cbc23-122">.NET Framework 4,5 yeniden dağıtılabilir programını çağırmak için komuttan gelen aşağıdaki çıkış kodları, kurulumun başarılı veya başarısız olup olmadığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cbc23-122">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="cbc23-123">0-Kurulum başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="cbc23-123">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="cbc23-124">3010 – Kurulum başarıyla tamamlandı; sistemin yeniden başlatılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="cbc23-124">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="cbc23-125">1602 – Kurulum iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cbc23-125">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="cbc23-126">Diğer tüm kodlar-kurulum hatalarla karşılaştı; Ayrıntılar için% Temp% konumunda oluşturulan günlük dosyalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="cbc23-126">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="cbc23-127">**Kurulum Iptal ediliyor**.</span><span class="sxs-lookup"><span data-stu-id="cbc23-127">**Canceling setup**.</span></span> <span data-ttu-id="cbc23-128">`Abort`, `m_downloadAbort` MIO bölümünde ve bayraklarını ayarlamak için yöntemini kullanarak istediğiniz zaman kurulumu iptal edebilirsiniz `m_ installAbort` .</span><span class="sxs-lookup"><span data-stu-id="cbc23-128">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="cbc23-129">Chainer örneği</span><span class="sxs-lookup"><span data-stu-id="cbc23-129">Chainer Sample</span></span>

<span data-ttu-id="cbc23-130">Chainer örneği sessizce başlatılır ve ilerleme durumunu gösterirken .NET Framework 4,5 kurulumunu izler.</span><span class="sxs-lookup"><span data-stu-id="cbc23-130">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="cbc23-131">Bu örnek, .NET Framework 4 için sunulan Chainer örneğine benzer.</span><span class="sxs-lookup"><span data-stu-id="cbc23-131">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="cbc23-132">Bununla birlikte, Ayrıca, .NET Framework 4 uygulamalarını kapatmak için ileti kutusunu işleyerek sistem yeniden başlatmalarının önlenmesine engel olabilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-132">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="cbc23-133">Bu ileti kutusu hakkında daha fazla bilgi için bkz. [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="cbc23-133">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="cbc23-134">Bu örneği .NET Framework 4 yükleyicisi ile birlikte kullanabilirsiniz; Bu senaryoda ileti yalnızca gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="cbc23-134">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="cbc23-135">Örneği yönetici olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-135">You must run the example as an administrator.</span></span>

<span data-ttu-id="cbc23-136">[.NET Framework 4,5 Chainer örneği](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) Için Visual Studio çözümünü tamamen MSDN Örnekleri Galerisi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-136">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="cbc23-137">Aşağıdaki bölümlerde bu örnekteki önemli dosyalar açıklanır: Mmıochainer. h, ChainingdotNet4. cpp ve ıprogressobserver. h.</span><span class="sxs-lookup"><span data-stu-id="cbc23-137">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="cbc23-138">Mmıochainer. h</span><span class="sxs-lookup"><span data-stu-id="cbc23-138">MMIOChainer.h</span></span>

- <span data-ttu-id="cbc23-139">Mmıochainer. h dosyası (bkz. [bütün kod](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) veri yapısı tanımını ve Chainer sınıfının türettiği temel sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-139">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="cbc23-140">4,5 .NET Framework, MıO veri yapısını .NET Framework 4,5 yükleyicisinin ihtiyacı olan verileri işleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-140">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="cbc23-141">MıO yapısında yapılan değişiklikler geriye dönük olarak uyumludur, bu nedenle .NET Framework 4 Chainer .NET Framework 4,5 kurulumu ile yeniden derleme gerekmeden çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-141">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="cbc23-142">Ancak, bu senaryo sistem yeniden başlatmaları azaltma özelliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cbc23-142">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="cbc23-143">Sürüm alanı, yapı ve ileti biçimindeki düzeltmeleri tanımlamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbc23-143">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="cbc23-144">.NET Framework kurulum, `VirtualQuery` Dosya eşlemesinin boyutunu belirleyen işlevi çağırarak Chainer arabiriminin sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="cbc23-144">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="cbc23-145">Boyut, sürüm alanına uyum sağlayacak kadar büyükse, .NET Framework Kurulum belirtilen değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-145">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="cbc23-146">Dosya eşlemesi, .NET Framework 4 ' te olduğu gibi bir sürüm alanı içeremeyecek kadar küçükse, kurulum işlemi 0 (4) sürümünü kabul eder.</span><span class="sxs-lookup"><span data-stu-id="cbc23-146">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="cbc23-147">Chainer .NET Framework kurulum 'un göndermek istediği iletinin sürümünü desteklemiyorsa, .NET Framework kurulum bir yoksayma yanıtı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="cbc23-147">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="cbc23-148">MıO veri yapısı aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="cbc23-148">The MMIO data structure is defined as follows:</span></span>

    ```cpp
    // MMIO data structure for interprocess communication
        struct MmioDataStructure
        {
            bool m_downloadFinished;               // Is download complete?
            bool m_installFinished;                // Is installation complete?
            bool m_downloadAbort;                  // Set to cause downloader to abort.
            bool m_installAbort;                   // Set to cause installer to abort.
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.
            HRESULT m_hrInternalError;
            WCHAR m_szCurrentItemStep[MAX_PATH];
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.

            BYTE m_version;                        // Version of the data structure, set by chainer:
                                                   // 0x0: .NET Framework 4
                                                   // 0x1: .NET Framework 4.5

            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.
        };
    ```

- <span data-ttu-id="cbc23-149">`MmioDataStructure`Veri yapısı doğrudan kullanılmamalıdır; `MmioChainer` Chainer 'ı uygulamak için yerine sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="cbc23-149">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="cbc23-150">`MmioChainer`.NET Framework 4,5 yeniden dağıtılabilir öğesini zincirlemek için sınıftan türetirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-150">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="cbc23-151">Iprogressobserver. h</span><span class="sxs-lookup"><span data-stu-id="cbc23-151">IProgressObserver.h</span></span>

- <span data-ttu-id="cbc23-152">Iprogressobserver. h dosyası bir ilerleme gözlemci uygular ([bkz. kodun tamamı](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span><span class="sxs-lookup"><span data-stu-id="cbc23-152">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="cbc23-153">Bu gözlemci, indirme ve yükleme ilerleme durumunu (işaretsiz `char` , 0-255% 1 ' i belirten %100) bildiren bir bildirim alır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-153">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="cbc23-154">Gözlemci bir ileti gönderdiğinde ve gözlemci bir yanıt göndermesi gerektiğinde, gözlemciye de bildirilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-154">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="cbc23-155">ChainingdotNet 4.5. cpp</span><span class="sxs-lookup"><span data-stu-id="cbc23-155">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="cbc23-156">[Chainingdotnet 4.5. cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) dosyası, `Server` `MmioChainer` sınıfından türetilen ve ilerleme bilgilerini göstermek için uygun yöntemleri geçersiz kılan sınıfını uygular.</span><span class="sxs-lookup"><span data-stu-id="cbc23-156">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="cbc23-157">Mmıochainer, belirtilen bölüm adına sahip bir bölüm oluşturur ve belirtilen olay adıyla Chainer 'yi başlatır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-157">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="cbc23-158">Olay adı, eşlenmiş veri yapısına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-158">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="cbc23-159">Bölüm ve olay adlarını benzersiz yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="cbc23-159">You should make the section and event names unique.</span></span> <span data-ttu-id="cbc23-160">`Server`Aşağıdaki koddaki sınıfı belirtilen kurulum programını başlatır, ilerlemesini izler ve bir çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cbc23-160">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="cbc23-161">Yükleme Main yönteminde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-161">The installation is started in the Main method.</span></span>

    ```cpp
    // Main entry point for program
    int __cdecl main(int argc, _In_count_(argc) char **_argv)
    {
        int result = 0;
        CString args;
        if (argc > 1)
        {
            args = CString(_argv[1]);
        }

        if (IsNetFx4Present(NETFX45_RC_REVISION))
        {
            printf(".NET Framework 4.5 is already installed");
        }
        else
        {
            result = Server().Launch(args);
        }

        return result;
    }
    ```

- <span data-ttu-id="cbc23-162">Yüklemeyi başlatmadan önce, bağlayıcı .NET Framework 4,5 ' ı çağırarak zaten yüklü olup olmadığını denetler `IsNetFx4Present` :</span><span class="sxs-lookup"><span data-stu-id="cbc23-162">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

    ```cpp
    ///  Checks for presence of the .NET Framework 4.
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.
    #define NETFX40_FULL_REVISION 0
    // TODO: Replace with released revision number
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5
    bool IsNetFx4Present(DWORD dwMinimumRelease)
    {
        DWORD dwError = ERROR_SUCCESS;
        HKEY hKey = NULL;
        DWORD dwData = 0;
        DWORD dwType = 0;
        DWORD dwSize = sizeof(dwData);

        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);
        if (ERROR_SUCCESS == dwError)
        {
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);

            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))
            {
                dwError = ERROR_INVALID_DATA;
            }
            else if (ERROR_FILE_NOT_FOUND == dwError)
            {
                // Release value was not found, let's check for 4.0.
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);

                // Install = (REG_DWORD)1;
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))
                {
                    // treat 4.0 as Release = 0
                    dwData = 0;
                }
                else
                {
                    dwError = ERROR_INVALID_DATA;
                }
            }
        }

        if (hKey != NULL)
        {
            ::RegCloseKey(hKey);
        }

        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));
    }
    ```

- <span data-ttu-id="cbc23-163">Doğru konumunu işaret etmek için yöntemindeki çalıştırılabilir dosyanın yolunu (örnekteki Setup.exe) değiştirebilir `Launch` veya konumu belirleyecek kodu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-163">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="cbc23-164">`MmioChainer`Temel sınıf, `Run()` türetilen sınıfın çağırdığı bir engelleme yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbc23-164">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

    ```cpp
    bool Launch(const CString& args)
    {
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run
    STARTUPINFO si = {0};
    si.cb = sizeof(si);
    PROCESS_INFORMATION pi = {0};

    // Launch the Setup.exe that installs the .NET Framework 4.5
    BOOL bLaunchedSetup = ::CreateProcess(NULL,
     cmdline.GetBuffer(),
     NULL, NULL, FALSE, 0, NULL, NULL,
     &si,
     &pi);

    // If successful
    if (bLaunchedSetup != 0)
    {
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);
    Run(pi.hProcess, observer);

    ……………………..
    return (bLaunchedSetup != 0);
    }
    ```

- <span data-ttu-id="cbc23-165">`Send`Yöntemi iletileri karşılar ve işler.</span><span class="sxs-lookup"><span data-stu-id="cbc23-165">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="cbc23-166">.NET Framework bu sürümünde, tek desteklenen ileti, kapatma uygulaması iletisidir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-166">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
            // Handle message
            switch (dwMessage)
            {
            case MMIO_CLOSE_APPS:
                {
                    printf("    applications are holding files in use:\n");
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)
                    {
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);
                    }

                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");
                    while (dwResult == 0)
                    {
                        switch (toupper(getwchar()))
                        {
                        case 'Y':
                            dwResult = IDYES;  // Close apps
                            break;
                        case 'N':
                            dwResult = IDNO;
                            break;
                        case 'R':
                            dwResult = IDRETRY;
                            break;
                        }
                    }
                    printf("\n");
                    break;
                }
            default:
                break;
            }
            printf("  response: %d\n  ", dwResult);
            return dwResult;
        }
    };
    ```

- <span data-ttu-id="cbc23-167">İlerleme verileri `char` 0 (%0) arasında işaretsiz ve 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="cbc23-167">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="cbc23-168">HRESULT `Finished` yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cbc23-168">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="cbc23-169">.NET Framework 4,5 yeniden dağıtılabilir, genellikle çok sayıda ilerleme iletisi ve tamamlanmayı belirten tek bir ileti yazar (Chainer tarafında).</span><span class="sxs-lookup"><span data-stu-id="cbc23-169">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="cbc23-170">Ayrıca, kayıtları arayarak zaman uyumsuz olarak okur `Abort` .</span><span class="sxs-lookup"><span data-stu-id="cbc23-170">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="cbc23-171">Bir kayıt alırsa, `Abort` yükleme işlemini iptal eder ve kurulum işlemleri geri alındıktan sonra verileri veri olarak E_ABORT bir tamamlanmış kayıt yazar.</span><span class="sxs-lookup"><span data-stu-id="cbc23-171">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="cbc23-172">Tipik bir sunucu, rastgele bir MıO dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde gösterildiği gibi `Server::CreateSection` ) ve yöntemini kullanarak yeniden dağıtılabilir ve `CreateProcess` yöntemi ile kanal adını geçirerek başlatır `-pipe someFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="cbc23-172">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="cbc23-173">Sunucu `OnProgress` , `Send` `Finished` uygulama arabirimine özgü kod ile, ve yöntemleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cbc23-173">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbc23-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbc23-174">See also</span></span>

- [<span data-ttu-id="cbc23-175">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cbc23-175">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="cbc23-176">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="cbc23-176">Deployment</span></span>](index.md)
