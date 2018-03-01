---
title: "Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c11d1c3469100b8bd0eb530a59bb3a01b152f3f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeniden dağıtılabilir çalışma zamanı. .NET Framework'ün bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun bir önkoşulu olarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kurulumunu dahil edebilirsiniz (bağlayabilirsiniz). Özelleştirilmiş veya birleştirilmiş kurulum deneyimi sunmak için sessizce başlatma isteyebilirsiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ve uygulamanızın Kurulum ilerleme gösterirken ilerleme durumunu izleyebilirsiniz. Sessiz izlemeyi etkinleştirmek için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (hangi izlenebilir) ayarı kurulumunuzu (İzleyici veya bağlayıcı) ile iletişim kurmak için bir bellek eşlemeli g/ç (olması) kesimini kullanarak bir protokol tanımlar. Bu protokol ilerleme durumu bilgileri elde etmek için ayrıntılı sonuçları almak, iletileri yanıtlayın ve iptal etmek bir bağlayıcı için bir yol tanımlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kurulumu.  
  
-   **Çağırma** .  Çağrılacak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Kurulum ve ilerleme durumu bilgileri olması bölümünden alırsınız, Kurulum programı aşağıdakileri yapmanız gerekir:  
  
    1.  Çağrı [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]yeniden dağıtılabilir programı:  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         Burada *bölüm adı* uygulamanızı tanımlamak için kullanmak istediğiniz herhangi bir addır. .NET framework kurulumunu okur ve olayları ve iletileri bu süre içinde kullanmak kullanışlı bulabileceğiniz şekilde olması bölümüne zaman uyumsuz olarak yazar. Örnekte, her ikisi de ayırdığını olması bölüm .NET Framework Kurulum işlemi oluşturucusu tarafından oluşturulan (`TheSectionName`) ve bir olay tanımlar (`TheEventName`):  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         Lütfen bu adlar, Kurulum programına benzersiz adlara sahip değiştirin.  
  
    2.  OLMASI bölümünden okuyun. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]'de, indirme ve yükleme işlemleri eşzamanlıdır: .NET Framework'ün bir bölümü indirilirken diğeri yüklenebilir. Sonuç olarak, ilerleme gönderilen (yani yazılan) olması bölüm iki sayı olarak geri (`m_downloadSoFar` ve `m_installSoFar`) 255 0'dan artırın. .NET Framework çıkar 255 olduğunda yazılır ve yükleme tamamlanmış demektir.  
  
-   **Çıkış kodları**. Çağırmak için komutu aşağıdaki çıkış kodları [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir program Kurulumu başarılı veya başarısız olana belirtin:  
  
    -   0 - Kurulum başarıyla tamamlandı.  
  
    -   3010 – Kurulum başarıyla tamamlandı; Sistem yeniden başlatma gereklidir.  
  
    -   1602 – Kurulumu iptal edildi.  
  
    -   Diğer tüm kodlar - Kurulum hatalarla karşılaştı; Ayrıntılar için % temp % içinde oluşturulan günlük dosyalarını inceleyin.  
  
-   **Kurulumu iptal etmek**. Kurulumu kullanarak dilediğiniz zaman iptal edebilirsiniz `Abort` ayarlamak için yöntemin `m_downloadAbort` ve `m_ installAbort` bayrakları olması bölümünde.  
  
## <a name="chainer-sample"></a>Bağlayıcı örneği  
 Bağlayıcı örneği sessizce başlatır ve izleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ilerleme durumunu gösteren sırasında Kurulum. Bu örnek, .NET Framework 4 için sağlanan bağlayıcı örnek benzerdir. Ancak, ek olarak, bu sistem yeniden başlatmalarını .NET Framework 4 uygulamaları kapatma ileti kutusu işleyerek önleyebilirsiniz. Bu ileti kutusu hakkında daha fazla bilgi için bkz: [azaltma sistemi yeniden sırasında .NET Framework 4.5 yüklemeleri](../../../docs/framework/deployment/reducing-system-restarts.md). Bu örnek ile .NET Framework 4 yükleyici kullanabilirsiniz; Bu senaryoda, yalnızca ileti gönderilmez.  
  
> [!WARNING]
>  Örnek bir yönetici olarak çalıştırmanız gerekir.  
  
 İçin eksiksiz bir Visual Studio çözüm indirebilirsiniz [.NET Framework 4.5 bağlayıcı örnek](http://go.microsoft.com/fwlink/?LinkId=231345) MSDN örnekleri galerisinden.  
  
 Aşağıdaki bölümlerde bu örnek önemli dosyalarında: MMIOChainer.h, ChainingdotNet4.cpp ve IProgressObserver.h.  
  
#### <a name="mmiochainerh"></a>MMIOChainer.h  
  
-   MMIOChainer.h dosyasını (bkz [tamamlamak kodu](http://go.microsoft.com/fwlink/?LinkId=231369)) veri yapısı tanımı ve kendisinden bağlayıcı türetilmiş sınıf temel sınıf içerir. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Verileri işlemek için olması veri yapısı genişletir, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yükleyici gerekiyor. Bir .NET Framework 4 bağlayıcı yeniden derlenmek gerek kalmadan .NET Framework 4.5 kurulum ile çalışabilmek için değişiklikleri olması yapısına yönelik işaretçinin geriye dönük uyumludur. Ancak, bu senaryo sistem yeniden başlatmalarını azaltmak için özelliğini desteklemiyor.  
  
     Sürüm alanı yapısı, ileti biçimi yapılan tanımlamanın bir yol sağlar.  .NET Framework kurulumunu çağırarak bağlayıcı arabirimi sürümünü belirler `VirtualQuery` dosya eşleme boyutunu belirlemek için işlev.  Boyutu sürüm alanı uyabilecek kadar büyük ise, .NET Framework kurulumunu belirtilen değeri kullanır. Dosya eşleme .NET Framework 4 ile söz konusu olduğu sürüm alanı içermesi için çok küçük ise Kurulum işlemi sürümü 0 (4) varsayar. Bağlayıcı göndermek için .NET Framework kurulumunu istediği ileti sürümü desteklemiyorsa, .NET Framework kurulumunu yoksay yanıt varsayar.  
  
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
  
-   `MmioDataStructure` Veri yapısı doğrudan kullanılmamalıdır; kullanın `MmioChainer` bunun yerine, bağlayıcı uygulamak için sınıf. Öğesinden türetilen `MmioChainer` zinciri sınıfına [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir.  
  
#### <a name="iprogressobserverh"></a>IProgressObserver.h  
  
-   Bir ilerleme gözlemci IProgressObserver.h dosya uygular ([tam kod bkz](http://go.microsoft.com/fwlink/?LinkId=231370)). Bu gözlemci indirme ve yükleme ilerleme durumunu bildirimde (imzasız belirtilen `char`, 0-255, % 1-% 100 tam gösteren). Gözlemci chainee ileti gönderir ve gözlemci yanıt göndermesi gerektiğini de bildirilir.  
  
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
  
-   [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) dosya uygulayan `Server` türeyen sınıf `MmioChainer` sınıfı ve ilerleme durumu bilgileri görüntülemek için uygun yöntemlerini geçersiz kılar. MmioChainer belirtilen bölüm adı taşıyan bir bölüm oluşturur ve belirtilen olay adıyla bağlayıcı başlatır. Olay adı eşlenen veri yapısı kaydedilir. Bölüm ve olay adları benzersiz olması. `Server` Sınıfı aşağıdaki kodda belirtilen Kurulum programını başlatır, ilerleme durumunu izler ve bir çıkış kodu döndürür.  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     Main yöntemi yükleme başlatıldı.  
  
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
  
-   İçinde çalıştırılabilir dosyanın (örnekte Setup.exe) yolu değiştirebilirsiniz `Launch` doğru konuma yönlendirmek veya konumunu belirlemek için kod özelleştirmek için bir yöntem. `MmioChainer` Temel sınıf sağlar bir engelleme `Run()` türetilmiş sınıf çağıran yöntemi.  
  
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
  
-   `Send` Yöntemi durdurur ve iletileri işler.  .NET Framework'ün bu sürümünde yalnızca desteklenen iletisi Kapat uygulama iletidir.  
  
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
    >  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeniden dağıtılabilir genellikle birçok ilerleme durumu iletileri ve tamamlanma (Bağlayıcı taraftaki) belirten tek bir ileti yazar. Bu da zaman uyumsuz olarak aramakta okur `Abort` kaydeder. Bunu alırsa bir `Abort` kayıt, yüklemeyi iptal eder ve yükleme durduruldu ve kurulum işlemlerini alındı geri sonra E_ABORT tamamlanmış bir kayıtla verilerini yazar.  
  
 Tipik bir sunucu bir rastgele olması dosya adı oluşturur, bir dosya oluşturur (önceki kod örneğinde gösterildiği gibi `Server::CreateSection`) ve yeniden dağıtılabilir kullanarak başlatan `CreateProcess` yöntemi ve kanal geçirme adı ile `-pipe someFileSectionName` seçeneği. Sunucu uygulamalıdır `OnProgress`, `Send`, ve `Finished` uygulama kullanıcı Arabirimi özgü kodu yöntemleriyle.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Dağıtım](../../../docs/framework/deployment/index.md)
