---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990059"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator, özel kanal uygulamalarınızı yapılandırma sistemine sunmak için kullanabileceğiniz bir araçtır. Bu, özel kanalınızın kullanıcılarının, `NetTcpBinding` `TcpTransportBindingElement`veya kullanarak özel bir bağlama gibi sistem tarafından sağlanmış bir bağlamayı yapılandırdıkları gibi bir. config dosyası kullanarak kanalınızı yapılandırmasına olanak sağlar.  
  
 Bir özel kanal yazdığınızda `BindingElement` ve bunu yeni bir veya `Binding`kullanarak programlama modelinde kullanıma sundığınızda, bir. config dosyası kullanarak `BindingElement` veya `Binding` yapılandırılabilir hale getirmek için bir sınıf kümesi oluşturmanız gerekir. Bu sınıfları oluşturmak ve müşterinizin deneyimini geliştirmek için ConfigurationCodeGenerator aracını kullanabilirsiniz.  
  
### <a name="to-build-the-tool"></a>Aracı oluşturmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Çözümün oluşturulması bir dosya oluşturur: ConfigurationCodeGenerator. exe. SampleRun. cmd dosyası, bu aracın [taşıma için sınıfları oluşturmak üzere nasıl kullanılacağını gösteren örnek bir komut satırına sahiptir: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
1. Komut isteminde, hem özel `BindingElement` bir tür hem de özel `Binding` bir tür varsa aşağıdakini yazın:  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Ya da yalnızca özel `BindingElement` bir tür varsa şunları yazın:  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Ya da yalnızca özel `Binding` bir tür varsa şunları yazın:  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Komut için `BindingElement` üç. cs dosyası (/be: Option belirttiyseniz), standart `Binding` için beş. cs dosyası (/SB: Option belirttiyseniz) ve bir. xml dosyası oluşturur.  
  
    1. /İn seçeneğini kullandıysanız,. cs dosyalarından biri bağlama öğesi `BindingElementExtensionSection` için öğesini uygular. Bu kod, diğer `BindingElement` özel Bağlamalarınızın bağlama öğesini kullanabilmesi için yapılandırma sistemine bunu gösterir. Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır. Dosyalar, varsayılan `//TODO` değerleri güncelleştirmenizi hatırlatmak için yorumlardır.  
  
    2. /SB seçeneğini belirlediyseniz,. cs dosyalarından ikisi `StandardBindingElement` `StandardBindingCollectionElement` sırasıyla bir ve, yapılandırma sistemine standart bağlamayı sunan bir ve uygular. Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır. Dosyalar, varsayılan `//TODO` değerleri güncelleştirmenizi hatırlatmak için yorumlardır.  
  
         /SB: seçeneğini belirlediyseniz, CodeToAddTo\<. >. cs, standart bağlamayı uygulayan sınıfa el ile eklemeniz gereken bir kod içerir.  
  
     SampleConfig. xml dosyası, önceki 1 veya 2. adımda tanımlanan işleyicileri kaydeden yapılandırma dosyasına eklemeniz gereken yapılandırma kodunu içerir.  
