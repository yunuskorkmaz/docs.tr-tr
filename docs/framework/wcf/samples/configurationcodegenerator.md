---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 97197926db0b44f1ad36e2eba6ab6bec42eced33
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342017"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="e966f-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="e966f-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="e966f-103">ConfigurationCodeGenerator yapılandırma sistemi için özel kanal uygulamaları göstermek için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e966f-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="e966f-104">Bu, kanalınızı yalnızca bunlar sistem tarafından sağlanan gibi bağlama yapılandırırsınız .config dosyasını kullanarak yapılandırmak, kullanıcıların, özel bir kanal sağlar `NetTcpBinding` veya özel bir bağlama kullanarak `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="e966f-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="e966f-105">Ne zaman özel bir kanalda yazma ve bunu yeni bir kullanarak programlama modeli için kullanıma `BindingElement` veya `Binding`, yapmak için sınıf kümesi oluşturmalısınız `BindingElement` veya `Binding` .config dosyası kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e966f-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="e966f-106">Bu sınıfları oluşturmak ve müşteri deneyimini geliştirmek için ConfigurationCodeGenerator Aracı'nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e966f-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="e966f-107">Aracı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="e966f-107">To build the tool</span></span>  
  
1. <span data-ttu-id="e966f-108">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e966f-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e966f-109">Çözümü derledikten bir dosya oluşturur: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="e966f-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="e966f-110">' % S'dosyası SampleRun.cmd sınıfları oluşturmak için bu aracı kullanmayı gösteren bir örnek komut satırı sahip [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e966f-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="e966f-111">Aracı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e966f-111">To run the tool</span></span>  
  
1. <span data-ttu-id="e966f-112">Komut isteminde aşağıdaki komutu yazın, bu iki özel varsa `BindingElement` türünü ve özel bir `Binding` türü:</span><span class="sxs-lookup"><span data-stu-id="e966f-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="e966f-113">Veya yalnızca özel varsa aşağıdaki komutu yazın `BindingElement` türü:</span><span class="sxs-lookup"><span data-stu-id="e966f-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="e966f-114">Veya yalnızca özel varsa aşağıdaki komutu yazın `Binding` türü:</span><span class="sxs-lookup"><span data-stu-id="e966f-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="e966f-115">Komut için üç .cs dosyası üretir `BindingElement` (belirttiyseniz / olması: seçeneği), standart için beş .cs dosya `Binding` (/sb belirtilmişse: seçeneği) ve bir .xml dosyası.</span><span class="sxs-lookup"><span data-stu-id="e966f-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1.  <span data-ttu-id="e966f-116">.cs birini uygular, /be seçeneğini kullandıysanız, dosyaları `BindingElementExtensionSection` , bağlama öğesi için.</span><span class="sxs-lookup"><span data-stu-id="e966f-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="e966f-117">Bu kod kullanıma sunar, `BindingElement` yapılandırma sistemi için özel diğer bağlamalar, bağlama öğesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e966f-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="e966f-118">Diğer dosyalar Varsayılanları ve sabitleri temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="e966f-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="e966f-119">Dosyalarınız `//TODO` , varsayılan değerleri güncelleştirmek için hatırlatmak için açıklama.</span><span class="sxs-lookup"><span data-stu-id="e966f-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2.  <span data-ttu-id="e966f-120">/Sb seçeneğini belirttiyseniz, iki .cs dosyaların uygulayan bir `StandardBindingElement` ve `StandardBindingCollectionElement` sırasıyla, yapılandırma sistemi, standart bağlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e966f-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="e966f-121">Diğer dosyalar Varsayılanları ve sabitleri temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="e966f-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="e966f-122">Dosyalarınız `//TODO` , varsayılan değerleri güncelleştirmek için hatırlatmak için açıklama.</span><span class="sxs-lookup"><span data-stu-id="e966f-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="e966f-123">/Sb belirtilmişse: CodeToAddTo seçeneği\<*YourStdBinding*> .cs standart bağlamanız uygulayan bir sınıf içinde el ile eklemelisiniz koduna sahip.</span><span class="sxs-lookup"><span data-stu-id="e966f-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="e966f-124">SampleConfig.xml dosya önceki adımda 1 veya 2 tanımlı işleyicileri kaydeden yapılandırma dosyasına eklemeniz gereken yapılandırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e966f-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
