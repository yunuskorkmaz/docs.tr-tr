---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: a01300024f89a0a189045d80622121f7db739a39
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912404"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator yapılandırma sistemi için özel kanal uygulamaları göstermek için kullanabileceğiniz bir araçtır. Bu, kanalınızı yalnızca bunlar sistem tarafından sağlanan gibi bağlama yapılandırırsınız .config dosyasını kullanarak yapılandırmak, kullanıcıların, özel bir kanal sağlar `NetTcpBinding` veya özel bir bağlama kullanarak `TcpTransportBindingElement`.  
  
 Ne zaman özel bir kanalda yazma ve bunu yeni bir kullanarak programlama modeli için kullanıma `BindingElement` veya `Binding`, yapmak için sınıf kümesi oluşturmalısınız `BindingElement` veya `Binding` .config dosyası kullanılarak yapılandırılabilir. Bu sınıfları oluşturmak ve müşteri deneyimini geliştirmek için ConfigurationCodeGenerator Aracı'nı kullanabilirsiniz.  
  
### <a name="to-build-the-tool"></a>Aracı yapılandırmak için  
  
1. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Çözümü derledikten bir dosya oluşturur: ConfigurationCodeGenerator.exe. ' % S'dosyası SampleRun.cmd sınıfları oluşturmak için bu aracı kullanmayı gösteren bir örnek komut satırı sahip [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
1. Komut isteminde aşağıdaki komutu yazın, bu iki özel varsa `BindingElement` türünü ve özel bir `Binding` türü:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Veya yalnızca özel varsa aşağıdaki komutu yazın `BindingElement` türü:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Veya yalnızca özel varsa aşağıdaki komutu yazın `Binding` türü:  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Komut için üç .cs dosyası üretir `BindingElement` (belirttiyseniz / olması: seçeneği), standart için beş .cs dosya `Binding` (/sb belirtilmişse: seçeneği) ve bir .xml dosyası.  
  
    1. .cs birini uygular, /be seçeneğini kullandıysanız, dosyaları `BindingElementExtensionSection` , bağlama öğesi için. Bu kod kullanıma sunar, `BindingElement` yapılandırma sistemi için özel diğer bağlamalar, bağlama öğesi kullanabilirsiniz. Diğer dosyalar Varsayılanları ve sabitleri temsil eden sınıfları içerir. Dosyalarınız `//TODO` , varsayılan değerleri güncelleştirmek için hatırlatmak için açıklama.  
  
    2. /Sb seçeneğini belirttiyseniz, iki .cs dosyaların uygulayan bir `StandardBindingElement` ve `StandardBindingCollectionElement` sırasıyla, yapılandırma sistemi, standart bağlamayı gösterir. Diğer dosyalar Varsayılanları ve sabitleri temsil eden sınıfları içerir. Dosyalarınız `//TODO` , varsayılan değerleri güncelleştirmek için hatırlatmak için açıklama.  
  
         /Sb belirtilmişse: CodeToAddTo seçeneği\<*YourStdBinding*> .cs standart bağlamanız uygulayan bir sınıf içinde el ile eklemelisiniz koduna sahip.  
  
     SampleConfig.xml dosya önceki adımda 1 veya 2 tanımlı işleyicileri kaydeden yapılandırma dosyasına eklemeniz gereken yapılandırma kodunu içerir.  
