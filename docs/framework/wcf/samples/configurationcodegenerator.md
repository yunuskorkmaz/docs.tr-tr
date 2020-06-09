---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: d64be95f71f840e08ede63e1c1f14ee08e52ce97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592482"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator, özel kanal uygulamalarınızı yapılandırma sistemine sunmak için kullanabileceğiniz bir araçtır. Bu, özel kanalınızın kullanıcılarının `NetTcpBinding` , veya kullanarak özel bir bağlama gibi sistem tarafından sağlanmış bir bağlamayı yapılandırdıkları gibi bir. config dosyası kullanarak kanalınızı yapılandırmasına olanak sağlar `TcpTransportBindingElement` .  
  
 Bir özel kanal yazdığınızda ve bunu yeni bir veya kullanarak programlama modelinde kullanıma sundığınızda, bir `BindingElement` `Binding` `BindingElement` `Binding` . config dosyası kullanarak veya yapılandırılabilir hale getirmek için bir sınıf kümesi oluşturmanız gerekir. Bu sınıfları oluşturmak ve müşterinizin deneyimini geliştirmek için ConfigurationCodeGenerator aracını kullanabilirsiniz.  
  
### <a name="to-build-the-tool"></a>Aracı oluşturmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Çözümün oluşturulması bir dosya oluşturur: ConfigurationCodeGenerator. exe. SampleRun. cmd dosyası, [taşıma: UDP](transport-udp.md) örneği için sınıfları oluşturmak üzere bu aracın nasıl kullanılacağını gösteren örnek bir komut satırına sahiptir.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
1. Komut isteminde, hem özel bir `BindingElement` tür hem de özel bir tür varsa aşağıdakini yazın `Binding` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Ya da yalnızca özel bir tür varsa şunları yazın `BindingElement` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Ya da yalnızca özel bir tür varsa şunları yazın `Binding` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Komut için üç. cs dosyası `BindingElement` (/be: Option belirttiyseniz), standart için beş. cs dosyası `Binding` (/SB: Option belirttiyseniz) ve bir. xml dosyası oluşturur.  
  
    1. /İn seçeneğini kullandıysanız,. cs dosyalarından biri `BindingElementExtensionSection` bağlama öğesi için öğesini uygular. Bu kod `BindingElement` , diğer özel Bağlamalarınızın bağlama öğesini kullanabilmesi için yapılandırma sistemine bunu gösterir. Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır. Dosyalar, `//TODO` varsayılan değerleri güncelleştirmenizi hatırlatmak için yorumlardır.  
  
    2. /SB seçeneğini belirlediyseniz,. cs dosyalarından ikisi `StandardBindingElement` sırasıyla bir ve `StandardBindingCollectionElement` , yapılandırma sistemine standart bağlamayı sunan bir ve uygular. Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır. Dosyalar, `//TODO` varsayılan değerleri güncelleştirmenizi hatırlatmak için yorumlardır.  
  
         /SB: seçeneğini belirlediyseniz CodeToAddTo. cs ' nin \<*YourStdBinding*> Standart bağlamayı uygulayan sınıfa el ile eklemeniz gereken kodu vardır.  
  
     SampleConfig. xml dosyası, önceki 1 veya 2. adımda tanımlanan işleyicileri kaydeden yapılandırma dosyasına eklemeniz gereken yapılandırma kodunu içerir.  
