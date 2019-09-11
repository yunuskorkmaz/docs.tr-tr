---
title: 'Nasıl yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c71816b1bd2e9c95e8c7efb44e3e689dce4ab93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853965"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="0b300-102">Nasıl yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="0b300-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="0b300-103">.NET Framework 4,5 yeniden dağıtılabilir bir çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="0b300-103">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="0b300-104">.NET Framework bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun önkoşul bir parçası olarak, (zincir) .NET Framework 4,5 kurulumunu dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b300-104">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="0b300-105">Özelleştirilmiş veya Birleşik bir kurulum deneyimi sunmak için, .NET Framework 4,5 kurulumunu sessizce başlatmak ve uygulamanızın kurulum ilerlemesini gösterirken ilerlemesini izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b300-105">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="0b300-106">Sessiz izlemeyi etkinleştirmek için, .NET Framework 4,5 kurulumu (izlenen), kurulumla iletişim kurmak için bellek eşlemeli g/ç (MıO) kesimini kullanarak bir protokolü tanımlar (izleyici veya bağlayıcı).</span><span class="sxs-lookup"><span data-stu-id="0b300-106">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="0b300-107">Bu protokol, bir Chainer 'ın ilerleme bilgilerini elde etme, ayrıntılı sonuçlar alma, iletilere yanıt verme ve .NET Framework 4,5 kurulumunu iptal etme yolunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b300-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="0b300-108">**Çağırma**.</span><span class="sxs-lookup"><span data-stu-id="0b300-108">**Invocation**.</span></span> <span data-ttu-id="0b300-109">.NET Framework 4,5 kurulumunu çağırmak ve MıO bölümünden ilerleme bilgileri almak için kurulum programınızın aşağıdakileri yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="0b300-109">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="0b300-110">.NET Framework 4,5 yeniden dağıtılabilir programını çağırın:</span><span class="sxs-lookup"><span data-stu-id="0b300-110">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="0b300-111">Burada *bölüm adı* uygulamanızı tanımlamak için kullanmak istediğiniz addır.</span><span class="sxs-lookup"><span data-stu-id="0b300-111">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="0b300-112">.NET Framework kurulum, MıO bölümünü zaman uyumsuz olarak okur ve yazar, bu nedenle bu süre içinde olayları ve iletileri kullanmayı kullanışlı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b300-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="0b300-113">Örnekte, .NET Framework kurulum işlemi her ikisi de MIO bölümünü (`TheSectionName`) ayıran ve bir olayı (`TheEventName`) tanımlayan bir Oluşturucu tarafından oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="0b300-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="0b300-114">Lütfen bu adları kurulum programınızın benzersiz adlarıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0b300-114">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="0b300-115">MıO bölümünden okuyun.</span><span class="sxs-lookup"><span data-stu-id="0b300-115">Read from the MMIO section.</span></span> <span data-ttu-id="0b300-116">.NET Framework 4,5 ' de, indirme ve yükleme işlemleri eşzamanlı olarak bulunur: .NET Framework bir kısmı, başka bir bölüm indirilirken yüklenmeye çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-116">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="0b300-117">Sonuç olarak, devam eden (`m_downloadSoFar` ve `m_installSoFar`) 0 ile 255 arasında bir artış olan MIO bölümüne geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="0b300-118">255 yazıldığında ve .NET Framework çıktığında yükleme tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0b300-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="0b300-119">**Çıkış kodları**.</span><span class="sxs-lookup"><span data-stu-id="0b300-119">**Exit codes**.</span></span> <span data-ttu-id="0b300-120">.NET Framework 4,5 yeniden dağıtılabilir programını çağırmak için komuttan gelen aşağıdaki çıkış kodları, kurulumun başarılı veya başarısız olup olmadığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="0b300-120">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="0b300-121">0-Kurulum başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0b300-121">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="0b300-122">3010 – Kurulum başarıyla tamamlandı; sistemin yeniden başlatılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="0b300-122">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="0b300-123">1602 – Kurulum iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0b300-123">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="0b300-124">Diğer tüm kodlar-kurulum hatalarla karşılaştı; Ayrıntılar için% Temp% konumunda oluşturulan günlük dosyalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="0b300-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="0b300-125">**Kurulum Iptal ediliyor**.</span><span class="sxs-lookup"><span data-stu-id="0b300-125">**Canceling setup**.</span></span> <span data-ttu-id="0b300-126">, `m_ installAbort` `Abort` MIObölümündevebayraklarınıayarlamakiçinyönteminikullanarakistediğinizzamankurulumuiptaledebilirsiniz.`m_downloadAbort`</span><span class="sxs-lookup"><span data-stu-id="0b300-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="0b300-127">Chainer örneği</span><span class="sxs-lookup"><span data-stu-id="0b300-127">Chainer Sample</span></span>

<span data-ttu-id="0b300-128">Chainer örneği sessizce başlatılır ve ilerleme durumunu gösterirken .NET Framework 4,5 kurulumunu izler.</span><span class="sxs-lookup"><span data-stu-id="0b300-128">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="0b300-129">Bu örnek, .NET Framework 4 için sunulan Chainer örneğine benzer.</span><span class="sxs-lookup"><span data-stu-id="0b300-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="0b300-130">Bununla birlikte, Ayrıca, .NET Framework 4 uygulamalarını kapatmak için ileti kutusunu işleyerek sistem yeniden başlatmalarının önlenmesine engel olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="0b300-131">Bu ileti kutusu hakkında daha fazla bilgi için bkz. [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="0b300-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="0b300-132">Bu örneği .NET Framework 4 yükleyicisi ile birlikte kullanabilirsiniz; Bu senaryoda ileti yalnızca gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="0b300-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="0b300-133">Örneği yönetici olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b300-133">You must run the example as an administrator.</span></span>

<span data-ttu-id="0b300-134">[.NET Framework 4,5 Chainer örneği](https://go.microsoft.com/fwlink/?LinkId=231345) Için Visual Studio çözümünü tamamen MSDN Örnekleri Galerisi ' nden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b300-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="0b300-135">Aşağıdaki bölümlerde bu örnekteki önemli dosyalar açıklanır: Mmıochainer. h, ChainingdotNet4. cpp ve ıprogressobserver. h.</span><span class="sxs-lookup"><span data-stu-id="0b300-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="0b300-136">Mmıochainer. h</span><span class="sxs-lookup"><span data-stu-id="0b300-136">MMIOChainer.h</span></span>

- <span data-ttu-id="0b300-137">Mmıochainer. h dosyası (bkz. [bütün kod](https://go.microsoft.com/fwlink/?LinkId=231369)) veri yapısı tanımını ve Chainer sınıfının türettiği temel sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="0b300-137">The MMIOChainer.h file (see [complete code](https://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="0b300-138">4,5 .NET Framework, MıO veri yapısını .NET Framework 4,5 yükleyicisinin ihtiyacı olan verileri işleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="0b300-138">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="0b300-139">MıO yapısında yapılan değişiklikler geriye dönük olarak uyumludur, bu nedenle .NET Framework 4 Chainer .NET Framework 4,5 kurulumu ile yeniden derleme gerekmeden çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="0b300-140">Ancak, bu senaryo sistem yeniden başlatmaları azaltma özelliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0b300-140">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="0b300-141">Sürüm alanı, yapı ve ileti biçimindeki düzeltmeleri tanımlamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b300-141">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="0b300-142">.NET Framework kurulum, dosya eşlemesinin boyutunu belirleyen `VirtualQuery` işlevi çağırarak Chainer arabiriminin sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="0b300-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="0b300-143">Boyut, sürüm alanına uyum sağlayacak kadar büyükse, .NET Framework Kurulum belirtilen değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b300-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="0b300-144">Dosya eşlemesi, .NET Framework 4 ' te olduğu gibi bir sürüm alanı içeremeyecek kadar küçükse, kurulum işlemi 0 (4) sürümünü kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0b300-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="0b300-145">Chainer .NET Framework kurulum 'un göndermek istediği iletinin sürümünü desteklemiyorsa, .NET Framework kurulum bir yoksayma yanıtı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="0b300-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="0b300-146">MıO veri yapısı aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="0b300-146">The MMIO data structure is defined as follows:</span></span>

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

- <span data-ttu-id="0b300-147">Veri yapısı doğrudan kullanılmamalıdır; Chainer 'ı uygulamak için yerine `MmioChainer` sınıfını kullanın. `MmioDataStructure`</span><span class="sxs-lookup"><span data-stu-id="0b300-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="0b300-148">.NET Framework 4,5 yeniden dağıtılabilir öğesini zincirlemek için sınıftantüretirsiniz.`MmioChainer`</span><span class="sxs-lookup"><span data-stu-id="0b300-148">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="0b300-149">Iprogressobserver. h</span><span class="sxs-lookup"><span data-stu-id="0b300-149">IProgressObserver.h</span></span>

- <span data-ttu-id="0b300-150">Iprogressobserver. h dosyası bir ilerleme gözlemci uygular ([bkz. kodun tamamı](https://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="0b300-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="0b300-151">Bu gözlemci, indirme ve yükleme ilerleme durumunu (işaretsiz `char`, 0-255% 1 ' i belirten% 100) bildiren bir bildirim alır.</span><span class="sxs-lookup"><span data-stu-id="0b300-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="0b300-152">Gözlemci bir ileti gönderdiğinde ve gözlemci bir yanıt göndermesi gerektiğinde, gözlemciye de bildirilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="0b300-153">ChainingdotNet 4.5. cpp</span><span class="sxs-lookup"><span data-stu-id="0b300-153">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="0b300-154">[Chainingdotnet 4.5. cpp](https://go.microsoft.com/fwlink/?LinkId=231368) dosyası, `MmioChainer` sınıfından türetilen `Server` ve ilerleme bilgilerini göstermek için uygun yöntemleri geçersiz kılan sınıfını uygular.</span><span class="sxs-lookup"><span data-stu-id="0b300-154">The [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="0b300-155">Mmıochainer, belirtilen bölüm adına sahip bir bölüm oluşturur ve belirtilen olay adıyla Chainer 'yi başlatır.</span><span class="sxs-lookup"><span data-stu-id="0b300-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="0b300-156">Olay adı, eşlenmiş veri yapısına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="0b300-157">Bölüm ve olay adlarını benzersiz yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="0b300-157">You should make the section and event names unique.</span></span> <span data-ttu-id="0b300-158">Aşağıdaki `Server` koddaki sınıfı belirtilen kurulum programını başlatır, ilerlemesini izler ve bir çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b300-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="0b300-159">Yükleme Main yönteminde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0b300-159">The installation is started in the Main method.</span></span>

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

- <span data-ttu-id="0b300-160">Yüklemeyi başlatmadan önce, bağlayıcı .NET Framework 4,5 ' ı çağırarak `IsNetFx4Present`zaten yüklü olup olmadığını denetler:</span><span class="sxs-lookup"><span data-stu-id="0b300-160">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

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

- <span data-ttu-id="0b300-161">Doğru konumunu işaret etmek için `Launch` yöntemindeki çalıştırılabilir dosyanın yolunu (örnekteki Setup. exe) değiştirebilir veya konumu belirleyecek kodu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b300-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="0b300-162">Temel sınıf, türetilen sınıfın çağırdığı `Run()` bir engelleme yöntemi sağlar. `MmioChainer`</span><span class="sxs-lookup"><span data-stu-id="0b300-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

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

- <span data-ttu-id="0b300-163">`Send` Yöntemi iletileri karşılar ve işler.</span><span class="sxs-lookup"><span data-stu-id="0b300-163">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="0b300-164">.NET Framework bu sürümünde, tek desteklenen ileti, kapatma uygulaması iletisidir.</span><span class="sxs-lookup"><span data-stu-id="0b300-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

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

- <span data-ttu-id="0b300-165">İlerleme verileri 0 (% `char` 0) arasında işaretsiz ve 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="0b300-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="0b300-166">HRESULT `Finished` yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0b300-166">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="0b300-167">.NET Framework 4,5 yeniden dağıtılabilir, genellikle çok sayıda ilerleme iletisi ve tamamlanmayı belirten tek bir ileti yazar (Chainer tarafında).</span><span class="sxs-lookup"><span data-stu-id="0b300-167">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="0b300-168">Ayrıca, `Abort` kayıtları arayarak zaman uyumsuz olarak okur.</span><span class="sxs-lookup"><span data-stu-id="0b300-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="0b300-169">Bir `Abort` kayıt alırsa, yükleme iptal edildikten ve kurulum işlemleri geri alındıktan sonra bu, yüklemeyi iptal eder ve E_ABORT ile tamamlanmış bir kayıt yazar.</span><span class="sxs-lookup"><span data-stu-id="0b300-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="0b300-170">Tipik bir sunucu, rastgele bir MIO dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde `Server::CreateSection`gösterildiği gibi) ve `CreateProcess` yöntemini kullanarak yeniden dağıtılabilir ve yöntemi ile `-pipe someFileSectionName` kanal adını geçirerek başlatır.</span><span class="sxs-lookup"><span data-stu-id="0b300-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="0b300-171">Sunucu, uygulama arabirimine `OnProgress`özgü `Send`kod ile `Finished` , ve yöntemleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b300-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b300-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b300-172">See also</span></span>

- [<span data-ttu-id="0b300-173">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b300-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [<span data-ttu-id="0b300-174">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="0b300-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
