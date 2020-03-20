---
title: 'Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: cd81ad83aee80341d0334cfa8caa165b25ee0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716497"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="6d59c-102">Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="6d59c-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="6d59c-103">.NET Framework 4.5 yeniden dağıtılabilir bir çalışma süresidir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-103">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="6d59c-104">.NET Framework'ün bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun ön koşul bir parçası olarak (zincir) .NET Framework 4.5 kurulumunu ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-104">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="6d59c-105">Özelleştirilmiş veya birleştirilmiş bir kurulum deneyimi sunmak için ,NET Framework 4.5 kurulumunu sessizce başlatmak ve uygulamanızın kurulum ilerlemesini gösterirken ilerlemesini izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-105">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="6d59c-106">Sessiz izlemeyi etkinleştirmek için ,NET Framework 4.5 kurulumu (izlenebilir) kurulumunuzla (izleyici veya zincirleyici) iletişim kurmak için bellek eşlenmiş Bir G/Ç (MMIO) segmenti kullanarak bir protokol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-106">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="6d59c-107">Bu protokol, bir zincirleyicinin ilerleme bilgilerini elde etmesini, ayrıntılı sonuçlar almasını, iletileri yanıtlamasını ve .NET Framework 4.5 kurulumünü iptal etmesinin bir yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="6d59c-108">**Çağrı .**</span><span class="sxs-lookup"><span data-stu-id="6d59c-108">**Invocation**.</span></span> <span data-ttu-id="6d59c-109">.NET Framework 4.5 kurulumunu aramak ve MMIO bölümünden ilerleme bilgilerini almak için kurulum programınız aşağıdakileri yapmalıdır:</span><span class="sxs-lookup"><span data-stu-id="6d59c-109">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="6d59c-110">.NET Framework 4.5 yeniden dağıtılabilir programı arayın:</span><span class="sxs-lookup"><span data-stu-id="6d59c-110">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="6d59c-111">*Bölüm adının* uygulamanızı tanımlamak için kullanmak istediğiniz herhangi bir ad olduğu yerde.</span><span class="sxs-lookup"><span data-stu-id="6d59c-111">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="6d59c-112">.NET Framework kurulumu MMIO bölümüne eşit olarak okur ve yazar, bu nedenle bu süre içinde olayları ve mesajları kullanmayı uygun bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="6d59c-113">Örnekte, .NET Framework kurulum işlemi, her ikisi de MMIO bölümünü`TheSectionName`() ayıran ve`TheEventName`bir olayı tanımlayan bir oluşturucu tarafından oluşturulur ( ):</span><span class="sxs-lookup"><span data-stu-id="6d59c-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="6d59c-114">Lütfen bu adları kurulum programınıza özgü adlarla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6d59c-114">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="6d59c-115">MMIO bölümünden okuyun.</span><span class="sxs-lookup"><span data-stu-id="6d59c-115">Read from the MMIO section.</span></span> <span data-ttu-id="6d59c-116">.NET Framework 4.5'te, indirme ve yükleme işlemleri eş zamanlıdır: .NET Framework'ün bir bölümü yüklenirken diğer bölümü yükleniyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-116">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="6d59c-117">Sonuç olarak, ilerleme 0'dan 255'e kadar olan iki sayı`m_downloadSoFar` `m_installSoFar`(ve ) olarak MMIO bölümüne geri gönderilir (yani yazılıdır).</span><span class="sxs-lookup"><span data-stu-id="6d59c-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="6d59c-118">255 yazıldığında ve .NET Framework çıktığında yükleme tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="6d59c-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="6d59c-119">**Çıkış kodları.**</span><span class="sxs-lookup"><span data-stu-id="6d59c-119">**Exit codes**.</span></span> <span data-ttu-id="6d59c-120">.NET Framework 4.5 yeniden dağıtılabilir programı aramak için komuttan aşağıdaki çıkış kodları, kurulumun başarılı olup olmadığını veya başarısız olup olmadığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6d59c-120">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="6d59c-121">0 - Kurulum başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6d59c-121">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="6d59c-122">3010 – Kurulum başarıyla tamamlandı; bir sistem yeniden başlatma gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-122">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="6d59c-123">1602 - Kurulum iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="6d59c-123">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="6d59c-124">Diğer tüm kodlar - Kurulum hataları karşılaştı; ayrıntılar için %geçici% olarak oluşturulan günlük dosyalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="6d59c-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="6d59c-125">**Kurulumu iptal etme.**</span><span class="sxs-lookup"><span data-stu-id="6d59c-125">**Canceling setup**.</span></span> <span data-ttu-id="6d59c-126">MMIO bölümündeki `Abort` `m_downloadAbort` bayrakları ve `m_ installAbort` bayrakları ayarlamak için yöntemi kullanarak istediğiniz zaman kurulumu iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="6d59c-127">Chainer Örnek</span><span class="sxs-lookup"><span data-stu-id="6d59c-127">Chainer Sample</span></span>

<span data-ttu-id="6d59c-128">Chainer örneği ,ilerleme gösterirken .NET Framework 4.5 kurulumlarını sessizce başlatır ve izler.</span><span class="sxs-lookup"><span data-stu-id="6d59c-128">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="6d59c-129">Bu örnek .NET Framework 4 için sağlanan Chainer örneğine benzer.</span><span class="sxs-lookup"><span data-stu-id="6d59c-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="6d59c-130">Ancak, buna ek olarak, .NET Framework 4 uygulamalarını kapatmak için ileti kutusunu işleyerek sistemin yeniden başlatılmasını önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="6d59c-131">Bu ileti kutusu hakkında bilgi için [bkz.](reducing-system-restarts.md)</span><span class="sxs-lookup"><span data-stu-id="6d59c-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="6d59c-132">Bu örneği .NET Framework 4 yükleyicisi ile kullanabilirsiniz; bu senaryoda, ileti yalnızca gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="6d59c-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="6d59c-133">Örneği yönetici olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-133">You must run the example as an administrator.</span></span>

<span data-ttu-id="6d59c-134">[.NET Framework 4.5 Chainer Örneği](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) için tam Visual Studio çözümlerini MSDN Örnekleri Galerisi'nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="6d59c-135">Aşağıdaki bölümlerde bu örnekteki önemli dosyalar açıklayınız: MMIOChainer.h, ChainingdotNet4.cpp ve IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="6d59c-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="6d59c-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="6d59c-136">MMIOChainer.h</span></span>

- <span data-ttu-id="6d59c-137">MMIOChainer.h dosyası [(bkz. tam kod)](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)veri yapısı tanımını ve zincirleyici sınıfının türetilmesi gereken taban sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-137">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="6d59c-138">.NET Framework 4.5, .NET Framework 4.5 yükleyicisinin ihtiyaç duyduğu verileri işlemek için MMIO veri yapısını genişletir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-138">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="6d59c-139">MMIO yapısındaki değişiklikler geriye dönük uyumludur, bu nedenle .NET Framework 4 zincirleyici stoylaştırma gerektirmeden .NET Framework 4.5 kurulumu ile çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="6d59c-140">Ancak, bu senaryo sistem yeniden başlatmayı azaltmak için özelliği desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6d59c-140">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="6d59c-141">Sürüm alanı, yapı ve ileti biçimindedüzeltmeleri tanımlamanın bir aracını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-141">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="6d59c-142">.NET Framework kurulumu, dosya eşlemeboyutunu belirlemek için `VirtualQuery` işlevi arayarak zincirleyici arabiriminin sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="6d59c-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="6d59c-143">Boyut sürüm alanını sığdıracak kadar büyükse, .NET Framework kurulumu belirtilen değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d59c-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="6d59c-144">Dosya eşleme ,.NET Framework 4'ün de geçerli olduğu gibi bir sürüm alanı içeremeyecek kadar küçükse, kurulum işlemi sürüm 0 (4) varsayar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="6d59c-145">Zincirleyici,.NET Framework kurulumunun göndermek istediği iletisürümünü desteklemiyorsa, .NET Framework kurulumu bir yoksayma yanıtı varsayar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="6d59c-146">MMIO veri yapısı aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="6d59c-146">The MMIO data structure is defined as follows:</span></span>

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

- <span data-ttu-id="6d59c-147">Veri `MmioDataStructure` yapısı doğrudan kullanılmamalıdır; bunun `MmioChainer` yerine zincirleyici uygulamak için sınıf kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d59c-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="6d59c-148">.NET Framework `MmioChainer` 4.5 yeniden dağıtılabilir zinciriçin sınıftan türetin.</span><span class="sxs-lookup"><span data-stu-id="6d59c-148">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="6d59c-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="6d59c-149">IProgressObserver.h</span></span>

- <span data-ttu-id="6d59c-150">IProgressObserver.h dosyası bir ilerleme gözlemcisi uygular[(tam koda bakın).](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)</span><span class="sxs-lookup"><span data-stu-id="6d59c-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="6d59c-151">Bu gözlemci indirme ve yükleme ilerleme (imzasız `char`olarak belirtilen, 0-255,% 1-100 tam gösteren) bildirilir alır.</span><span class="sxs-lookup"><span data-stu-id="6d59c-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="6d59c-152">Chainee bir mesaj gönderdiğinde gözlemci ye de bildirilir ve gözlemci bir yanıt göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="6d59c-153">ZincirlemedotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="6d59c-153">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="6d59c-154">[ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) dosyası, `Server` `MmioChainer` sınıftan türetilen ve ilerleme bilgilerini görüntülemek için uygun yöntemleri geçersiz kılan sınıfı uygular.</span><span class="sxs-lookup"><span data-stu-id="6d59c-154">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="6d59c-155">MmioChainer belirtilen bölüm adı içeren bir bölüm oluşturur ve belirtilen olay adı ile zincirleyici yi alartır.</span><span class="sxs-lookup"><span data-stu-id="6d59c-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="6d59c-156">Olay adı eşlenen veri yapısına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="6d59c-157">Bölüm ve etkinlik adlarını benzersiz hale getirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-157">You should make the section and event names unique.</span></span> <span data-ttu-id="6d59c-158">Aşağıdaki `Server` koddaki sınıf belirtilen kurulum programını başlatır, ilerlemesini izler ve bir çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d59c-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="6d59c-159">Yükleme Ana yöntemde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="6d59c-159">The installation is started in the Main method.</span></span>

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

- <span data-ttu-id="6d59c-160">Yüklemeyi başlatmadan önce, zincirleyici .NET Framework 4.5'in zaten `IsNetFx4Present`arayarak yüklü olup olmadığını kontrol eder:</span><span class="sxs-lookup"><span data-stu-id="6d59c-160">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

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

- <span data-ttu-id="6d59c-161">`Launch` Yöntemdeki yürütülebilir (Örneğin Setup.exe) yolunu doğru konumuna işaret etmek için değiştirebilir veya konumu belirlemek için kodu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="6d59c-162">Taban `MmioChainer` sınıf, türemiş sınıfın çağırdığı bir engelleme `Run()` yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

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

- <span data-ttu-id="6d59c-163">Yöntem, `Send` iletileri yakalar ve işler.</span><span class="sxs-lookup"><span data-stu-id="6d59c-163">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="6d59c-164">.NET Framework'ün bu sürümünde desteklenen tek ileti yakın uygulama iletisidir.</span><span class="sxs-lookup"><span data-stu-id="6d59c-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

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

- <span data-ttu-id="6d59c-165">İlerleme verileri 0 `char` (%0) arasında imzasız ve 255 (%100).</span><span class="sxs-lookup"><span data-stu-id="6d59c-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="6d59c-166">HRESULT `Finished` yönteme aktarılır.</span><span class="sxs-lookup"><span data-stu-id="6d59c-166">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="6d59c-167">.NET Framework 4.5 yeniden dağıtılabilir genellikle birçok ilerleme iletisi ve tamamlanmasını gösteren tek bir ileti yazar (zincirleyici tarafında).</span><span class="sxs-lookup"><span data-stu-id="6d59c-167">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="6d59c-168">Ayrıca, kayıtları arıyor, `Abort` asynchronously okur.</span><span class="sxs-lookup"><span data-stu-id="6d59c-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="6d59c-169">Bir `Abort` kayıt alırsa, yüklemeyi iptal eder ve yükleme iptal edildikten ve kurulum işlemleri geri alındıktan sonra verileri olarak E_ABORT ile tamamlanmış bir kayıt yazar.</span><span class="sxs-lookup"><span data-stu-id="6d59c-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="6d59c-170">Tipik bir sunucu rasgele bir MMIO dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde gösterildiği gibi, içinde), `Server::CreateSection`ve `CreateProcess` yöntemi `-pipe someFileSectionName` kullanarak ve seçeneği ile boru adı geçerek yeniden dağıtılabilir başlattı.</span><span class="sxs-lookup"><span data-stu-id="6d59c-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="6d59c-171">Sunucu, `Send`uygulama Kullanıcı `Finished` Bira'ya özgü kod ile ve yöntemleri uygulamalıdır. `OnProgress`</span><span class="sxs-lookup"><span data-stu-id="6d59c-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d59c-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d59c-172">See also</span></span>

- [<span data-ttu-id="6d59c-173">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6d59c-173">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="6d59c-174">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="6d59c-174">Deployment</span></span>](index.md)
