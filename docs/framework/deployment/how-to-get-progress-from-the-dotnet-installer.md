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
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma

.NET Framework 4.5 yeniden dağıtılabilir bir çalışma süresidir. .NET Framework'ün bu sürümü için uygulamalar geliştirirseniz, uygulamanızın kurulumunun ön koşul bir parçası olarak (zincir) .NET Framework 4.5 kurulumunu ekleyebilirsiniz. Özelleştirilmiş veya birleştirilmiş bir kurulum deneyimi sunmak için ,NET Framework 4.5 kurulumunu sessizce başlatmak ve uygulamanızın kurulum ilerlemesini gösterirken ilerlemesini izlemek isteyebilirsiniz. Sessiz izlemeyi etkinleştirmek için ,NET Framework 4.5 kurulumu (izlenebilir) kurulumunuzla (izleyici veya zincirleyici) iletişim kurmak için bellek eşlenmiş Bir G/Ç (MMIO) segmenti kullanarak bir protokol tanımlar. Bu protokol, bir zincirleyicinin ilerleme bilgilerini elde etmesini, ayrıntılı sonuçlar almasını, iletileri yanıtlamasını ve .NET Framework 4.5 kurulumünü iptal etmesinin bir yolunu tanımlar.

- **Çağrı .** .NET Framework 4.5 kurulumunu aramak ve MMIO bölümünden ilerleme bilgilerini almak için kurulum programınız aşağıdakileri yapmalıdır:

    1. .NET Framework 4.5 yeniden dağıtılabilir programı arayın:

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        *Bölüm adının* uygulamanızı tanımlamak için kullanmak istediğiniz herhangi bir ad olduğu yerde. .NET Framework kurulumu MMIO bölümüne eşit olarak okur ve yazar, bu nedenle bu süre içinde olayları ve mesajları kullanmayı uygun bulabilirsiniz. Örnekte, .NET Framework kurulum işlemi, her ikisi de MMIO bölümünü`TheSectionName`() ayıran ve`TheEventName`bir olayı tanımlayan bir oluşturucu tarafından oluşturulur ( ):

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Lütfen bu adları kurulum programınıza özgü adlarla değiştirin.

    2. MMIO bölümünden okuyun. .NET Framework 4.5'te, indirme ve yükleme işlemleri eş zamanlıdır: .NET Framework'ün bir bölümü yüklenirken diğer bölümü yükleniyor olabilir. Sonuç olarak, ilerleme 0'dan 255'e kadar olan iki sayı`m_downloadSoFar` `m_installSoFar`(ve ) olarak MMIO bölümüne geri gönderilir (yani yazılıdır). 255 yazıldığında ve .NET Framework çıktığında yükleme tamamlanır.

- **Çıkış kodları.** .NET Framework 4.5 yeniden dağıtılabilir programı aramak için komuttan aşağıdaki çıkış kodları, kurulumun başarılı olup olmadığını veya başarısız olup olmadığını gösterir:

  - 0 - Kurulum başarıyla tamamlandı.

  - 3010 – Kurulum başarıyla tamamlandı; bir sistem yeniden başlatma gereklidir.

  - 1602 - Kurulum iptal edildi.

  - Diğer tüm kodlar - Kurulum hataları karşılaştı; ayrıntılar için %geçici% olarak oluşturulan günlük dosyalarını inceleyin.

- **Kurulumu iptal etme.** MMIO bölümündeki `Abort` `m_downloadAbort` bayrakları ve `m_ installAbort` bayrakları ayarlamak için yöntemi kullanarak istediğiniz zaman kurulumu iptal edebilirsiniz.

## <a name="chainer-sample"></a>Chainer Örnek

Chainer örneği ,ilerleme gösterirken .NET Framework 4.5 kurulumlarını sessizce başlatır ve izler. Bu örnek .NET Framework 4 için sağlanan Chainer örneğine benzer. Ancak, buna ek olarak, .NET Framework 4 uygulamalarını kapatmak için ileti kutusunu işleyerek sistemin yeniden başlatılmasını önleyebilir. Bu ileti kutusu hakkında bilgi için [bkz.](reducing-system-restarts.md) Bu örneği .NET Framework 4 yükleyicisi ile kullanabilirsiniz; bu senaryoda, ileti yalnızca gönderilmez.

> [!WARNING]
> Örneği yönetici olarak çalıştırmanız gerekir.

[.NET Framework 4.5 Chainer Örneği](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) için tam Visual Studio çözümlerini MSDN Örnekleri Galerisi'nden indirebilirsiniz.

Aşağıdaki bölümlerde bu örnekteki önemli dosyalar açıklayınız: MMIOChainer.h, ChainingdotNet4.cpp ve IProgressObserver.h.

#### <a name="mmiochainerh"></a>MMIOChainer.h

- MMIOChainer.h dosyası [(bkz. tam kod)](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)veri yapısı tanımını ve zincirleyici sınıfının türetilmesi gereken taban sınıfı içerir. .NET Framework 4.5, .NET Framework 4.5 yükleyicisinin ihtiyaç duyduğu verileri işlemek için MMIO veri yapısını genişletir. MMIO yapısındaki değişiklikler geriye dönük uyumludur, bu nedenle .NET Framework 4 zincirleyici stoylaştırma gerektirmeden .NET Framework 4.5 kurulumu ile çalışabilir. Ancak, bu senaryo sistem yeniden başlatmayı azaltmak için özelliği desteklemez.

    Sürüm alanı, yapı ve ileti biçimindedüzeltmeleri tanımlamanın bir aracını sağlar. .NET Framework kurulumu, dosya eşlemeboyutunu belirlemek için `VirtualQuery` işlevi arayarak zincirleyici arabiriminin sürümünü belirler. Boyut sürüm alanını sığdıracak kadar büyükse, .NET Framework kurulumu belirtilen değeri kullanır. Dosya eşleme ,.NET Framework 4'ün de geçerli olduğu gibi bir sürüm alanı içeremeyecek kadar küçükse, kurulum işlemi sürüm 0 (4) varsayar. Zincirleyici,.NET Framework kurulumunun göndermek istediği iletisürümünü desteklemiyorsa, .NET Framework kurulumu bir yoksayma yanıtı varsayar.

    MMIO veri yapısı aşağıdaki gibi tanımlanır:

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

- Veri `MmioDataStructure` yapısı doğrudan kullanılmamalıdır; bunun `MmioChainer` yerine zincirleyici uygulamak için sınıf kullanın. .NET Framework `MmioChainer` 4.5 yeniden dağıtılabilir zinciriçin sınıftan türetin.

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- IProgressObserver.h dosyası bir ilerleme gözlemcisi uygular[(tam koda bakın).](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592) Bu gözlemci indirme ve yükleme ilerleme (imzasız `char`olarak belirtilen, 0-255,% 1-100 tam gösteren) bildirilir alır. Chainee bir mesaj gönderdiğinde gözlemci ye de bildirilir ve gözlemci bir yanıt göndermelidir.

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>ZincirlemedotNet4.5.cpp

- [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) dosyası, `Server` `MmioChainer` sınıftan türetilen ve ilerleme bilgilerini görüntülemek için uygun yöntemleri geçersiz kılan sınıfı uygular. MmioChainer belirtilen bölüm adı içeren bir bölüm oluşturur ve belirtilen olay adı ile zincirleyici yi alartır. Olay adı eşlenen veri yapısına kaydedilir. Bölüm ve etkinlik adlarını benzersiz hale getirmelisiniz. Aşağıdaki `Server` koddaki sınıf belirtilen kurulum programını başlatır, ilerlemesini izler ve bir çıkış kodu döndürür.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Yükleme Ana yöntemde başlatılır.

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

- Yüklemeyi başlatmadan önce, zincirleyici .NET Framework 4.5'in zaten `IsNetFx4Present`arayarak yüklü olup olmadığını kontrol eder:

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

- `Launch` Yöntemdeki yürütülebilir (Örneğin Setup.exe) yolunu doğru konumuna işaret etmek için değiştirebilir veya konumu belirlemek için kodu özelleştirebilirsiniz. Taban `MmioChainer` sınıf, türemiş sınıfın çağırdığı bir engelleme `Run()` yöntemi sağlar.

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

- Yöntem, `Send` iletileri yakalar ve işler. .NET Framework'ün bu sürümünde desteklenen tek ileti yakın uygulama iletisidir.

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

- İlerleme verileri 0 `char` (%0) arasında imzasız ve 255 (%100).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- HRESULT `Finished` yönteme aktarılır.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > .NET Framework 4.5 yeniden dağıtılabilir genellikle birçok ilerleme iletisi ve tamamlanmasını gösteren tek bir ileti yazar (zincirleyici tarafında). Ayrıca, kayıtları arıyor, `Abort` asynchronously okur. Bir `Abort` kayıt alırsa, yüklemeyi iptal eder ve yükleme iptal edildikten ve kurulum işlemleri geri alındıktan sonra verileri olarak E_ABORT ile tamamlanmış bir kayıt yazar.

Tipik bir sunucu rasgele bir MMIO dosya adı oluşturur, dosyayı oluşturur (önceki kod örneğinde gösterildiği gibi, içinde), `Server::CreateSection`ve `CreateProcess` yöntemi `-pipe someFileSectionName` kullanarak ve seçeneği ile boru adı geçerek yeniden dağıtılabilir başlattı. Sunucu, `Send`uygulama Kullanıcı `Finished` Bira'ya özgü kod ile ve yöntemleri uygulamalıdır. `OnProgress`

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Dağıtım](index.md)
