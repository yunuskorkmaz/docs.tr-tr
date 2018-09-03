---
title: 'Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c27bdb75ef9950d0b2b32f742b38e141cf4981b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43472052"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="0fc84-102">Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="0fc84-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>
<span data-ttu-id="0fc84-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeniden dağıtılabilir bir çalışma zamanıdır.</span><span class="sxs-lookup"><span data-stu-id="0fc84-103">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is a redistributable runtime.</span></span> <span data-ttu-id="0fc84-104">.NET Framework'ün bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun bir önkoşulu olarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kurulumunu dahil edebilirsiniz (bağlayabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="0fc84-104">If you develop apps for this version of the .NET Framework, you can include (chain) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="0fc84-105">Özelleştirilmiş veya birleşik kurulum deneyimi sunmak için sessizce başlatmak isteyebilirsiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ve uygulamanızın Kurulum ilerleme gösterirken, ilerleme durumunu izleyin.</span><span class="sxs-lookup"><span data-stu-id="0fc84-105">To present a customized or unified setup experience, you may want to silently launch [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="0fc84-106">Sessiz izlemeyi etkinleştirmek için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (izlenebilir) Kurulumu kurulumunuzu (İzleyici veya chainer) ile iletişim kurmak için bir bellek eşlemeli g/ç (olması) kesimini kullanarak bir protokol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-106">To enable silent tracking, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="0fc84-107">Bu protokolün ilerleme durumu bilgileri elde etmek için ayrıntılı sonuçlar elde edin, iletilere yanıt verir ve iptal etmek bir bağlayıcı için bir yol tanımlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kurulumu.</span><span class="sxs-lookup"><span data-stu-id="0fc84-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup.</span></span>  
  
-   <span data-ttu-id="0fc84-108">**Çağırma** .</span><span class="sxs-lookup"><span data-stu-id="0fc84-108">**Invocation** .</span></span>  <span data-ttu-id="0fc84-109">Çağrılacak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ve olması bölümünden ilerleme bilgilerini alma, Kurulum programınız için aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0fc84-109">To call [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>  
  
    1.  <span data-ttu-id="0fc84-110">Çağrı [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]yeniden dağıtılabilir program:</span><span class="sxs-lookup"><span data-stu-id="0fc84-110">Call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:</span></span>  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         <span data-ttu-id="0fc84-111">Burada *bölüm adı* uygulamanızı tanımlamak için kullanmak istediğiniz herhangi bir ad olduğu.</span><span class="sxs-lookup"><span data-stu-id="0fc84-111">where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="0fc84-112">.NET framework kurulumunu okur ve olayları ve iletileri bu süre boyunca kullanmak kullanışlı bulabileceğiniz şekilde olması bölümüne zaman uyumsuz olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="0fc84-113">Örnekte, her ikisi de ayırma olması bölüm .NET Framework Kurulum sürecini Oluşturucu tarafından oluşturulan (`TheSectionName`) ve bir olayı tanımlar (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="0fc84-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         <span data-ttu-id="0fc84-114">Lütfen bu adları, Kurulum programınız için benzersiz bir ada değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0fc84-114">Please replace those names with names that are unique to your setup program.</span></span>  
  
    2.  <span data-ttu-id="0fc84-115">OLMASI bölümünden okuyun.</span><span class="sxs-lookup"><span data-stu-id="0fc84-115">Read from the MMIO section.</span></span> <span data-ttu-id="0fc84-116">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]'de, indirme ve yükleme işlemleri eşzamanlıdır: .NET Framework'ün bir bölümü indirilirken diğeri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-116">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="0fc84-117">Sonuç olarak, devam eden gönderilir (yani yazılmış) geri olması bölümüne iki sayı olarak (`m_downloadSoFar` ve `m_installSoFar`) 255 0'dan artırın.</span><span class="sxs-lookup"><span data-stu-id="0fc84-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="0fc84-118">255 zaman yazılmıştır ve .NET Framework çıkar yükleme tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0fc84-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>  
  
-   <span data-ttu-id="0fc84-119">**Çıkış kodlarını**.</span><span class="sxs-lookup"><span data-stu-id="0fc84-119">**Exit codes**.</span></span> <span data-ttu-id="0fc84-120">Çağırmak için komutu aşağıdaki çıkış kodlarını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir program kurulum başarılı veya başarısız olduğu gösterir:</span><span class="sxs-lookup"><span data-stu-id="0fc84-120">The following exit codes from the command to call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable program indicate whether setup has succeeded or failed:</span></span>  
  
    -   <span data-ttu-id="0fc84-121">0 - Kurulum başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0fc84-121">0 - Setup completed successfully.</span></span>  
  
    -   <span data-ttu-id="0fc84-122">3010 – Kurulum başarıyla tamamlandı; sistemin yeniden başlatılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="0fc84-122">3010 – Setup completed successfully; a system restart is required.</span></span>  
  
    -   <span data-ttu-id="0fc84-123">1602 – kurulum iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0fc84-123">1602 – Setup has been canceled.</span></span>  
  
    -   <span data-ttu-id="0fc84-124">Tüm diğer kodları - Kurulum hatalarla karşılaştı; Ayrıntılar için % temp % içinde oluşturulan günlük dosyalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="0fc84-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>  
  
-   <span data-ttu-id="0fc84-125">**Kurulum İptal**.</span><span class="sxs-lookup"><span data-stu-id="0fc84-125">**Canceling setup**.</span></span> <span data-ttu-id="0fc84-126">Kurulum kullanarak dilediğiniz zaman iptal edebilirsiniz `Abort` ayarlanacak yöntemi `m_downloadAbort` ve `m_ installAbort` olması bölümünde bayrakları.</span><span class="sxs-lookup"><span data-stu-id="0fc84-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>  
  
## <a name="chainer-sample"></a><span data-ttu-id="0fc84-127">Bağlayıcı örneği</span><span class="sxs-lookup"><span data-stu-id="0fc84-127">Chainer Sample</span></span>  
 <span data-ttu-id="0fc84-128">Bağlayıcı örneği sessizce başlatır ve izleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ilerleme durumunu gösteren oluştu.</span><span class="sxs-lookup"><span data-stu-id="0fc84-128">The Chainer sample silently launches and tracks [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup while showing progress.</span></span> <span data-ttu-id="0fc84-129">Bu örnek, .NET Framework 4 için sağlanan bağlayıcı örneği benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="0fc84-130">Ancak, ayrıca, bu sistem yeniden başlatmalarını .NET Framework 4 uygulamaları kapatmak için ileti kutusu işleyerek önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc84-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="0fc84-131">Bu ileti kutusu hakkında daha fazla bilgi için bkz. [azaltma sistemi yeniden sırasında .NET Framework 4.5 yüklemeleri](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="0fc84-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="0fc84-132">Bu örnek ile .NET Framework 4 yükleyici kullanabilirsiniz; Bu senaryoda, yalnızca ileti gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="0fc84-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0fc84-133">Örneğin, bir yönetici olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-133">You must run the example as an administrator.</span></span>  
  
 <span data-ttu-id="0fc84-134">İçin tam Visual Studio çözümünü indirebilir [.NET Framework 4.5 bağlayıcı örneği](https://go.microsoft.com/fwlink/?LinkId=231345) MSDN Örnekler Galerisi.</span><span class="sxs-lookup"><span data-stu-id="0fc84-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>  
  
 <span data-ttu-id="0fc84-135">Aşağıdaki bölümlerde bu önemli dosyaları: Mmıochainer.h ChainingdotNet4.cpp ve Iprogressobserver.h.</span><span class="sxs-lookup"><span data-stu-id="0fc84-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>  
  
#### <a name="mmiochainerh"></a><span data-ttu-id="0fc84-136">Mmıochainer.h</span><span class="sxs-lookup"><span data-stu-id="0fc84-136">MMIOChainer.h</span></span>  
  
-   <span data-ttu-id="0fc84-137">Mmıochainer.h dosyası (bkz [tamamlamak kod](https://go.microsoft.com/fwlink/?LinkId=231369)) veri yapısı tanımını ve kendisinden bağlayıcı sınıfın türetilmesi temel sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-137">The MMIOChainer.h file (see [complete code](https://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="0fc84-138">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Olması veri yapısı, verilerin işlenmesini genişletir, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yükleyici gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-138">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] extends the MMIO data structure to handle data that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] installer needs.</span></span> <span data-ttu-id="0fc84-139">OLMASI yapısı değişiklikler geriye dönük olarak uyumlu, olduğundan bir .NET Framework 4 bağlayıcı kurulumu .NET Framework 4.5 yeniden derleme gerek kalmadan çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fc84-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="0fc84-140">Ancak, bu senaryo, özellik sistem yeniden başlatmalarını azaltmak için desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0fc84-140">However, this scenario does not support the feature for reducing system restarts.</span></span>  
  
     <span data-ttu-id="0fc84-141">Sürümü alanı yapısı, ileti biçimi düzeltmeleri tanımlayan bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-141">A version field provides a means of identifying revisions to the structure and message format.</span></span>  <span data-ttu-id="0fc84-142">.NET Framework kurulumunu çağırarak chainer arabirimi sürümünü belirler `VirtualQuery` dosya eşleme boyutunu belirlemek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="0fc84-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span>  <span data-ttu-id="0fc84-143">Sürüm alanı tutabilecek kadar büyük boyutudur, .NET Framework kurulumunu belirtilen değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0fc84-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="0fc84-144">Dosya eşlemesi ile .NET Framework 4 Bu durum bir sürümü alanı içeren çok küçükse, Kurulum işlemi sürümü 0 (4) varsayar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="0fc84-145">Bağlayıcı göndermek için .NET Framework kurulumunu isteyen ileti sürümü desteklemiyorsa, .NET Framework kurulumunu yoksay yanıt varsayar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>  
  
     <span data-ttu-id="0fc84-146">OLMASI veri yapısı şu şekilde tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="0fc84-146">The MMIO data structure is defined as follows:</span></span>  
  
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
  
-   <span data-ttu-id="0fc84-147">`MmioDataStructure` Veri yapısına doğrudan kullanılmamalıdır; kullanan `MmioChainer` bunun yerine, bağlayıcı uygulamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0fc84-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="0fc84-148">Öğesinden türetilen `MmioChainer` zinciri sınıfına [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-148">Derive from the `MmioChainer` class to chain the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span></span>  
  
#### <a name="iprogressobserverh"></a><span data-ttu-id="0fc84-149">Iprogressobserver.h</span><span class="sxs-lookup"><span data-stu-id="0fc84-149">IProgressObserver.h</span></span>  
  
-   <span data-ttu-id="0fc84-150">Iprogressobserver.h dosyası bir ilerleme gözlemcisi uygular ([tam kod bkz](https://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="0fc84-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="0fc84-151">Bu gözlemci indirme ve yükleme ilerlemesini bildirim (imzasız belirtilen `char`, 0-255 gösteren 1-%100 tamamlandı).</span><span class="sxs-lookup"><span data-stu-id="0fc84-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="0fc84-152">Gözlemci ayrıca chainee bir ileti gönderir ve gözlemci yanıt göndermesi gerektiğini bildirilir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="0fc84-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="0fc84-153">ChainingdotNet4.5.cpp</span></span>  
  
-   <span data-ttu-id="0fc84-154">[ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) dosya uygular `Server` türetilen sınıf `MmioChainer` sınıfı ve ilerleme bilgisini görüntülemek için uygun yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-154">The [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="0fc84-155">MmioChainer belirtilen bölüm adı ile bir bölüm oluşturur ve belirtilen olay adıyla chainer başlatır.</span><span class="sxs-lookup"><span data-stu-id="0fc84-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="0fc84-156">Olay adı, eşlenmiş veri yapısı olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="0fc84-157">Bölümü ve olay adları benzersiz olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-157">You should make the section and event names unique.</span></span> <span data-ttu-id="0fc84-158">`Server` Aşağıdaki kodda sınıfı belirtilen Kurulum programı başlatan, ilerleme durumunu izler ve bir çıkış kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fc84-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     <span data-ttu-id="0fc84-159">Yüklemesi Main yöntemine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0fc84-159">The installation is started in the Main method.</span></span>  
  
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
  
-   <span data-ttu-id="0fc84-160">Yüklemeyi başlatmadan önce bağlayıcı bakar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] çağırarak zaten yüklüyse `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="0fc84-160">Before launching the installation, the chainer checks to see if the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is already installed by calling `IsNetFx4Present`:</span></span>  
  
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
  
-   <span data-ttu-id="0fc84-161">Yürütülebilir dosya (örnekte Setup.exe) yolunu değiştirebileceğiniz `Launch` , doğru konuma işaret veya konumunu belirlemek için kod özelleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fc84-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="0fc84-162">`MmioChainer` Taban sınıfı sağlar bir engelleme `Run()` türetilmiş sınıf çağıran yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fc84-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>  
  
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
  
-   <span data-ttu-id="0fc84-163">`Send` Yöntemi durdurur ve iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="0fc84-163">The `Send` method intercepts and processes the messages.</span></span>  <span data-ttu-id="0fc84-164">.NET Framework'ün bu sürümünde, yalnızca desteklenen uygulama kapatma iletisi iletisidir.</span><span class="sxs-lookup"><span data-stu-id="0fc84-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
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
  
-   <span data-ttu-id="0fc84-165">İlerleme verilerdir imzasız `char` (% 0) 0 ile 255 (% 100) arasında.</span><span class="sxs-lookup"><span data-stu-id="0fc84-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   <span data-ttu-id="0fc84-166">HRESULT geçirilir `Finished` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fc84-166">The HRESULT is passed to the `Finished` method.</span></span>  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0fc84-167">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeniden dağıtılabilir genellikle birçok ilerleme iletilerini ve tamamlama (Bağlayıcı tarafında) gösteren tek bir ileti yazar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-167">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="0fc84-168">Ayrıca zaman uyumsuz olarak aranırken okuduğu `Abort` kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0fc84-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="0fc84-169">Bunu alırsa bir `Abort` kayıt, yükleme işlemini iptal ve sonra yükleme iptal edildi ve Kurulum işlem geri alındı E_ABORT tamamlanmış bir kayıtla verilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="0fc84-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>  
  
 <span data-ttu-id="0fc84-170">Tipik bir sunucu bir rastgele olması dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde gösterildiği gibi `Server::CreateSection`) ve yeniden dağıtılabilir kullanarak başlatır `CreateProcess` adı yöntemi ve kanal geçirme ile `-pipe someFileSectionName` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0fc84-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="0fc84-171">Sunucu uygulamalıdır `OnProgress`, `Send`, ve `Finished` uygulama UI özgü kodla yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0fc84-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc84-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0fc84-172">See Also</span></span>  
 [<span data-ttu-id="0fc84-173">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0fc84-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="0fc84-174">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="0fc84-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
