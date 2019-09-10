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
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Nasıl yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma

.NET Framework 4,5 yeniden dağıtılabilir bir çalışma zamanı. .NET Framework bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun önkoşul bir parçası olarak, (zincir) .NET Framework 4,5 kurulumunu dahil edebilirsiniz. Özelleştirilmiş veya Birleşik bir kurulum deneyimi sunmak için, .NET Framework 4,5 kurulumunu sessizce başlatmak ve uygulamanızın kurulum ilerlemesini gösterirken ilerlemesini izlemek isteyebilirsiniz. Sessiz izlemeyi etkinleştirmek için, .NET Framework 4,5 kurulumu (izlenen), kurulumla iletişim kurmak için bellek eşlemeli g/ç (MıO) kesimini kullanarak bir protokolü tanımlar (izleyici veya bağlayıcı). Bu protokol, bir Chainer 'ın ilerleme bilgilerini elde etme, ayrıntılı sonuçlar alma, iletilere yanıt verme ve .NET Framework 4,5 kurulumunu iptal etme yolunu tanımlar.

- **Çağırma**. .NET Framework 4,5 kurulumunu çağırmak ve MıO bölümünden ilerleme bilgileri almak için kurulum programınızın aşağıdakileri yapması gerekir:

    1. .NET Framework 4,5 yeniden dağıtılabilir programını çağırın:

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        Burada *bölüm adı* uygulamanızı tanımlamak için kullanmak istediğiniz addır. .NET Framework kurulum, MıO bölümünü zaman uyumsuz olarak okur ve yazar, bu nedenle bu süre içinde olayları ve iletileri kullanmayı kullanışlı bulabilirsiniz. Örnekte, .NET Framework kurulum işlemi her ikisi de MIO bölümünü (`TheSectionName`) ayıran ve bir olayı (`TheEventName`) tanımlayan bir Oluşturucu tarafından oluşturulur:

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Lütfen bu adları kurulum programınızın benzersiz adlarıyla değiştirin.

    2. MıO bölümünden okuyun. .NET Framework 4,5 ' de, indirme ve yükleme işlemleri eşzamanlı olarak bulunur: .NET Framework bir kısmı, başka bir bölüm indirilirken yüklenmeye çalışıyor olabilir. Sonuç olarak, devam eden (`m_downloadSoFar` ve `m_installSoFar`) 0 ile 255 arasında bir artış olan MIO bölümüne geri gönderilir. 255 yazıldığında ve .NET Framework çıktığında yükleme tamamlanır.

- **Çıkış kodları**. .NET Framework 4,5 yeniden dağıtılabilir programını çağırmak için komuttan gelen aşağıdaki çıkış kodları, kurulumun başarılı veya başarısız olup olmadığını gösterir:

  - 0-Kurulum başarıyla tamamlandı.

  - 3010 – Kurulum başarıyla tamamlandı; sistemin yeniden başlatılması gerekiyor.

  - 1602 – Kurulum iptal edildi.

  - Diğer tüm kodlar-kurulum hatalarla karşılaştı; Ayrıntılar için% Temp% konumunda oluşturulan günlük dosyalarını inceleyin.

- **Kurulum Iptal ediliyor**. , `m_ installAbort` `Abort` MIObölümündevebayraklarınıayarlamakiçinyönteminikullanarakistediğinizzamankurulumuiptaledebilirsiniz.`m_downloadAbort`

## <a name="chainer-sample"></a>Chainer örneği

Chainer örneği sessizce başlatılır ve ilerleme durumunu gösterirken .NET Framework 4,5 kurulumunu izler. Bu örnek, .NET Framework 4 için sunulan Chainer örneğine benzer. Bununla birlikte, Ayrıca, .NET Framework 4 uygulamalarını kapatmak için ileti kutusunu işleyerek sistem yeniden başlatmalarının önlenmesine engel olabilir. Bu ileti kutusu hakkında daha fazla bilgi için bkz. [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](../../../docs/framework/deployment/reducing-system-restarts.md). Bu örneği .NET Framework 4 yükleyicisi ile birlikte kullanabilirsiniz; Bu senaryoda ileti yalnızca gönderilmez.

> [!WARNING]
> Örneği yönetici olarak çalıştırmanız gerekir.

[.NET Framework 4,5 Chainer örneği](https://go.microsoft.com/fwlink/?LinkId=231345) Için Visual Studio çözümünü tamamen MSDN Örnekleri Galerisi ' nden indirebilirsiniz.

Aşağıdaki bölümlerde bu örnekteki önemli dosyalar açıklanır: Mmıochainer. h, ChainingdotNet4. cpp ve ıprogressobserver. h.

#### <a name="mmiochainerh"></a>Mmıochainer. h

- Mmıochainer. h dosyası (bkz. [bütün kod](https://go.microsoft.com/fwlink/?LinkId=231369)) veri yapısı tanımını ve Chainer sınıfının türettiği temel sınıfı içerir. 4,5 .NET Framework, MıO veri yapısını .NET Framework 4,5 yükleyicisinin ihtiyacı olan verileri işleyecek şekilde genişletir. MıO yapısında yapılan değişiklikler geriye dönük olarak uyumludur, bu nedenle .NET Framework 4 Chainer .NET Framework 4,5 kurulumu ile yeniden derleme gerekmeden çalışabilir. Ancak, bu senaryo sistem yeniden başlatmaları azaltma özelliğini desteklemez.

    Sürüm alanı, yapı ve ileti biçimindeki düzeltmeleri tanımlamak için bir yol sağlar. .NET Framework kurulum, dosya eşlemesinin boyutunu belirleyen `VirtualQuery` işlevi çağırarak Chainer arabiriminin sürümünü belirler. Boyut, sürüm alanına uyum sağlayacak kadar büyükse, .NET Framework Kurulum belirtilen değeri kullanır. Dosya eşlemesi, .NET Framework 4 ' te olduğu gibi bir sürüm alanı içeremeyecek kadar küçükse, kurulum işlemi 0 (4) sürümünü kabul eder. Chainer .NET Framework kurulum 'un göndermek istediği iletinin sürümünü desteklemiyorsa, .NET Framework kurulum bir yoksayma yanıtı olduğunu varsayar.

    MıO veri yapısı aşağıdaki gibi tanımlanır:

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

- Veri yapısı doğrudan kullanılmamalıdır; Chainer 'ı uygulamak için yerine `MmioChainer` sınıfını kullanın. `MmioDataStructure` .NET Framework 4,5 yeniden dağıtılabilir öğesini zincirlemek için sınıftantüretirsiniz.`MmioChainer`

#### <a name="iprogressobserverh"></a>Iprogressobserver. h

- Iprogressobserver. h dosyası bir ilerleme gözlemci uygular ([bkz. kodun tamamı](https://go.microsoft.com/fwlink/?LinkId=231370)). Bu gözlemci, indirme ve yükleme ilerleme durumunu (işaretsiz `char`, 0-255% 1 ' i belirten% 100) bildiren bir bildirim alır. Gözlemci bir ileti gönderdiğinde ve gözlemci bir yanıt göndermesi gerektiğinde, gözlemciye de bildirilir.

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>ChainingdotNet 4.5. cpp

- [Chainingdotnet 4.5. cpp](https://go.microsoft.com/fwlink/?LinkId=231368) dosyası, `MmioChainer` sınıfından türetilen `Server` ve ilerleme bilgilerini göstermek için uygun yöntemleri geçersiz kılan sınıfını uygular. Mmıochainer, belirtilen bölüm adına sahip bir bölüm oluşturur ve belirtilen olay adıyla Chainer 'yi başlatır. Olay adı, eşlenmiş veri yapısına kaydedilir. Bölüm ve olay adlarını benzersiz yapmalısınız. Aşağıdaki `Server` koddaki sınıfı belirtilen kurulum programını başlatır, ilerlemesini izler ve bir çıkış kodu döndürür.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Yükleme Main yönteminde başlatılır.

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

- Yüklemeyi başlatmadan önce, bağlayıcı .NET Framework 4,5 ' ı çağırarak `IsNetFx4Present`zaten yüklü olup olmadığını denetler:

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

- Doğru konumunu işaret etmek için `Launch` yöntemindeki çalıştırılabilir dosyanın yolunu (örnekteki Setup. exe) değiştirebilir veya konumu belirleyecek kodu özelleştirebilirsiniz. Temel sınıf, türetilen sınıfın çağırdığı `Run()` bir engelleme yöntemi sağlar. `MmioChainer`

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

- `Send` Yöntemi iletileri karşılar ve işler. .NET Framework bu sürümünde, tek desteklenen ileti, kapatma uygulaması iletisidir.

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

- İlerleme verileri 0 (% `char` 0) arasında işaretsiz ve 255 (100%).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- HRESULT `Finished` yöntemine geçirilir.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > .NET Framework 4,5 yeniden dağıtılabilir, genellikle çok sayıda ilerleme iletisi ve tamamlanmayı belirten tek bir ileti yazar (Chainer tarafında). Ayrıca, `Abort` kayıtları arayarak zaman uyumsuz olarak okur. Bir `Abort` kayıt alırsa, yükleme iptal edildikten ve kurulum işlemleri geri alındıktan sonra bu, yüklemeyi iptal eder ve E_ABORT ile tamamlanmış bir kayıt yazar.

Tipik bir sunucu, rastgele bir MIO dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde `Server::CreateSection`gösterildiği gibi) ve `CreateProcess` yöntemini kullanarak yeniden dağıtılabilir ve yöntemi ile `-pipe someFileSectionName` kanal adını geçirerek başlatır. Sunucu, uygulama arabirimine `OnProgress`özgü `Send`kod ile `Finished` , ve yöntemleri uygulamalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Dağıtım](../../../docs/framework/deployment/index.md)
