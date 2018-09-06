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
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742676"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeniden dağıtılabilir bir çalışma zamanıdır. .NET Framework'ün bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun bir önkoşulu olarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kurulumunu dahil edebilirsiniz (bağlayabilirsiniz). Özelleştirilmiş veya birleşik kurulum deneyimi sunmak için sessizce başlatmak isteyebilirsiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ve uygulamanızın Kurulum ilerleme gösterirken, ilerleme durumunu izleyin. Sessiz izlemeyi etkinleştirmek için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (izlenebilir) Kurulumu kurulumunuzu (İzleyici veya chainer) ile iletişim kurmak için bir bellek eşlemeli g/ç (olması) kesimini kullanarak bir protokol tanımlar. Bu protokolün ilerleme durumu bilgileri elde etmek için ayrıntılı sonuçlar elde edin, iletilere yanıt verir ve iptal etmek bir bağlayıcı için bir yol tanımlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kurulumu.  
  
-   **Çağırma** .  Çağrılacak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ve olması bölümünden ilerleme bilgilerini alma, Kurulum programınız için aşağıdakileri yapmanız gerekir:  
  
    1.  Çağrı [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]yeniden dağıtılabilir program:  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         Burada *bölüm adı* uygulamanızı tanımlamak için kullanmak istediğiniz herhangi bir ad olduğu. .NET framework kurulumunu okur ve olayları ve iletileri bu süre boyunca kullanmak kullanışlı bulabileceğiniz şekilde olması bölümüne zaman uyumsuz olarak yazar. Örnekte, her ikisi de ayırma olması bölüm .NET Framework Kurulum sürecini Oluşturucu tarafından oluşturulan (`TheSectionName`) ve bir olayı tanımlar (`TheEventName`):  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         Lütfen bu adları, Kurulum programınız için benzersiz bir ada değiştirin.  
  
    2.  OLMASI bölümünden okuyun. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]'de, indirme ve yükleme işlemleri eşzamanlıdır: .NET Framework'ün bir bölümü indirilirken diğeri yüklenebilir. Sonuç olarak, devam eden gönderilir (yani yazılmış) geri olması bölümüne iki sayı olarak (`m_downloadSoFar` ve `m_installSoFar`) 255 0'dan artırın. 255 zaman yazılmıştır ve .NET Framework çıkar yükleme tamamlanır.  
  
-   **Çıkış kodlarını**. Çağırmak için komutu aşağıdaki çıkış kodlarını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir program kurulum başarılı veya başarısız olduğu gösterir:  
  
    -   0 - Kurulum başarıyla tamamlandı.  
  
    -   3010 – Kurulum başarıyla tamamlandı; sistemin yeniden başlatılması gerekiyor.  
  
    -   1602 – kurulum iptal edildi.  
  
    -   Tüm diğer kodları - Kurulum hatalarla karşılaştı; Ayrıntılar için % temp % içinde oluşturulan günlük dosyalarını inceleyin.  
  
-   **Kurulum İptal**. Kurulum kullanarak dilediğiniz zaman iptal edebilirsiniz `Abort` ayarlanacak yöntemi `m_downloadAbort` ve `m_ installAbort` olması bölümünde bayrakları.  
  
## <a name="chainer-sample"></a>Bağlayıcı örneği  
 Bağlayıcı örneği sessizce başlatır ve izleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ilerleme durumunu gösteren oluştu. Bu örnek, .NET Framework 4 için sağlanan bağlayıcı örneği benzerdir. Ancak, ayrıca, bu sistem yeniden başlatmalarını .NET Framework 4 uygulamaları kapatmak için ileti kutusu işleyerek önleyebilirsiniz. Bu ileti kutusu hakkında daha fazla bilgi için bkz. [azaltma sistemi yeniden sırasında .NET Framework 4.5 yüklemeleri](../../../docs/framework/deployment/reducing-system-restarts.md). Bu örnek ile .NET Framework 4 yükleyici kullanabilirsiniz; Bu senaryoda, yalnızca ileti gönderilmez.  
  
> [!WARNING]
>  Örneğin, bir yönetici olarak çalıştırmanız gerekir.  
  
 İçin tam Visual Studio çözümünü indirebilir [.NET Framework 4.5 bağlayıcı örneği](https://go.microsoft.com/fwlink/?LinkId=231345) MSDN Örnekler Galerisi.  
  
 Aşağıdaki bölümlerde bu önemli dosyaları: Mmıochainer.h ChainingdotNet4.cpp ve Iprogressobserver.h.  
  
#### <a name="mmiochainerh"></a>Mmıochainer.h  
  
-   Mmıochainer.h dosyası (bkz [tamamlamak kod](https://go.microsoft.com/fwlink/?LinkId=231369)) veri yapısı tanımını ve kendisinden bağlayıcı sınıfın türetilmesi temel sınıfı içerir. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Olması veri yapısı, verilerin işlenmesini genişletir, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yükleyici gerekir. OLMASI yapısı değişiklikler geriye dönük olarak uyumlu, olduğundan bir .NET Framework 4 bağlayıcı kurulumu .NET Framework 4.5 yeniden derleme gerek kalmadan çalışabilirsiniz. Ancak, bu senaryo, özellik sistem yeniden başlatmalarını azaltmak için desteklemez.  
  
     Sürümü alanı yapısı, ileti biçimi düzeltmeleri tanımlayan bir yol sağlar.  .NET Framework kurulumunu çağırarak chainer arabirimi sürümünü belirler `VirtualQuery` dosya eşleme boyutunu belirlemek için işlevi.  Sürüm alanı tutabilecek kadar büyük boyutudur, .NET Framework kurulumunu belirtilen değeri kullanır. Dosya eşlemesi ile .NET Framework 4 Bu durum bir sürümü alanı içeren çok küçükse, Kurulum işlemi sürümü 0 (4) varsayar. Bağlayıcı göndermek için .NET Framework kurulumunu isteyen ileti sürümü desteklemiyorsa, .NET Framework kurulumunu yoksay yanıt varsayar.  
  
     OLMASI veri yapısı şu şekilde tanımlanır:  
  
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
  
-   `MmioDataStructure` Veri yapısına doğrudan kullanılmamalıdır; kullanan `MmioChainer` bunun yerine, bağlayıcı uygulamak için sınıf. Öğesinden türetilen `MmioChainer` zinciri sınıfına [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir.  
  
#### <a name="iprogressobserverh"></a>Iprogressobserver.h  
  
-   Iprogressobserver.h dosyası bir ilerleme gözlemcisi uygular ([tam kod bkz](https://go.microsoft.com/fwlink/?LinkId=231370)). Bu gözlemci indirme ve yükleme ilerlemesini bildirim (imzasız belirtilen `char`, 0-255 gösteren 1-%100 tamamlandı). Gözlemci ayrıca chainee bir ileti gönderir ve gözlemci yanıt göndermesi gerektiğini bildirilir.  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a>ChainingdotNet4.5.cpp  
  
-   [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) dosya uygular `Server` türetilen sınıf `MmioChainer` sınıfı ve ilerleme bilgisini görüntülemek için uygun yöntemleri geçersiz kılar. MmioChainer belirtilen bölüm adı ile bir bölüm oluşturur ve belirtilen olay adıyla chainer başlatır. Olay adı, eşlenmiş veri yapısı olarak kaydedilir. Bölümü ve olay adları benzersiz olmanız gerekir. `Server` Aşağıdaki kodda sınıfı belirtilen Kurulum programı başlatan, ilerleme durumunu izler ve bir çıkış kodu döndürür.  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     Yüklemesi Main yöntemine başlatılır.  
  
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
  
-   Yüklemeyi başlatmadan önce bağlayıcı bakar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] çağırarak zaten yüklüyse `IsNetFx4Present`:  
  
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
  
-   Yürütülebilir dosya (örnekte Setup.exe) yolunu değiştirebileceğiniz `Launch` , doğru konuma işaret veya konumunu belirlemek için kod özelleştirmek için yöntemi. `MmioChainer` Taban sınıfı sağlar bir engelleme `Run()` türetilmiş sınıf çağıran yöntemi.  
  
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
  
-   `Send` Yöntemi durdurur ve iletileri işler.  .NET Framework'ün bu sürümünde, yalnızca desteklenen uygulama kapatma iletisi iletisidir.  
  
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
  
-   İlerleme verilerdir imzasız `char` (% 0) 0 ile 255 (% 100) arasında.  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   HRESULT geçirilir `Finished` yöntemi.  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeniden dağıtılabilir genellikle birçok ilerleme iletilerini ve tamamlama (Bağlayıcı tarafında) gösteren tek bir ileti yazar. Ayrıca zaman uyumsuz olarak aranırken okuduğu `Abort` kaydeder. Bunu alırsa bir `Abort` kayıt, yükleme işlemini iptal ve sonra yükleme iptal edildi ve Kurulum işlem geri alındı E_ABORT tamamlanmış bir kayıtla verilerini yazar.  
  
 Tipik bir sunucu bir rastgele olması dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde gösterildiği gibi `Server::CreateSection`) ve yeniden dağıtılabilir kullanarak başlatır `CreateProcess` adı yöntemi ve kanal geçirme ile `-pipe someFileSectionName` seçeneği. Sunucu uygulamalıdır `OnProgress`, `Send`, ve `Finished` uygulama UI özgü kodla yöntemleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Dağıtım](../../../docs/framework/deployment/index.md)
