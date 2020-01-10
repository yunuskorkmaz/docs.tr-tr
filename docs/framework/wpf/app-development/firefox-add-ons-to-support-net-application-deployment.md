---
title: .NET Uygulaması Dağıtımını Destekleyen Firefox Eklentileri
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 687f61bd3ec7d10c6aa66c20cd5eb58fcc56f18a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636373"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET Uygulaması Dağıtımını Destekleyen Firefox Eklentileri
Firefox için Windows Presentation Foundation (WPF) eklentisi ve Firefox .NET Framework Yardımcısı, XAML tarayıcı uygulamaları (XBAP), gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve ClickOnce uygulamalarının Mozilla Firefox tarayıcısı ile çalışmasını sağlar.  
  
## <a name="wpf-plug-in-for-firefox"></a>Firefox için WPF eklentisi  
 Firefox WPF eklentisi, XBAP ve gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalarının, en üst düzeyde veya Firefox tarayıcısında bir HTML IFRAME 'de gezinip çalışmasına olanak sağlar. XBAP, bir Web sunucusuna yayımlanabilir ve desteklenen tarayıcılarda başlatılabilir olan bir WPF uygulamasıdır. Gevşek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bir XML dosyası gibi desteklenen tarayıcılarda gezinilebilir ve görüntülenebilir.  
  
 Firefox WPF eklentisi .NET Framework 3,5 ile yüklenir. 7\. pencere, 3,5 .NET Framework içerir, ancak Firefox WPF eklentisini içermez. Windows 7 ' de Firefox için WPF eklentisini yükleyemezsiniz.  
  
 .NET Framework 4, Firefox WPF eklentisini içermez. Ancak, 3,5 ve .NET Framework 4 .NET Framework her ikisi de yüklüyse, Firefox WPF eklentisi .NET Framework 3,5 ile yüklenir. Bu nedenle .NET Framework 4 uygulama çalışmaya devam eder çünkü WPF ana bilgisayarı doğru Framework sürümünü yükleyecek. Daha fazla bilgi için bkz. [WPF konağı (PresentationHost. exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>Firefox için .NET Framework Assistant  
 Firefox .NET Framework Yardımcısı, tek başına ClickOnce uygulamalarının Firefox tarayıcısından çalıştırılmasını sağlar. Firefox .NET Framework Yardımcısı, Firefox tarayıcısından önce ve sonra yüklendiğinde aynı şekilde çalışır. Firefox tarayıcısı başlatıldığında ve .NET Framework 3,5 SP1 yüklendiğinde, Firefox Firefox için .NET Framework yardımcısını bulur ve kurar. Kullanıcılar Firefox .NET Framework yardımcısını aşağıdakileri yapmak üzere yapılandırabilir:  
  
- ClickOnce uygulamasını çalıştırmadan önce sor.  
  
- .NET Framework yüklü tüm sürümlerini veya yalnızca en son sürümü bildirin.  
  
 Firefox için .NET Framework Yardımcısı, .NET Framework 3,5 SP1 'e dahildir. Firefox .NET Framework yardımcısını kaldırma hakkında daha fazla bilgi için bkz. [Firefox için .NET Framework yardımcısını kaldırma](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulaması Dağıtma](deploying-a-wpf-application-wpf.md)
- [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](wpf-xaml-browser-applications-overview.md)
- [Firefox WPF Eklentisinin Yüklü Olup Olmadığını Algılama](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
